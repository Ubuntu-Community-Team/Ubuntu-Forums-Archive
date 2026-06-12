---
title: "can not rmmod kernel module after snull_tx some data"
date: 2014-07-24
forum: Ubuntu Dev Link Forum
---

### Post by zerop2 on 2014-07-24
i open a layer 2 program to wait to receive frame in another console

in current console, i send frame with snull_tx with eth0, but after insmod this module,
i can not rmmod it 

nothing to receive to see in another console

how to send and recv correctly in this case?

```

#ifndef __KERNEL__
#  define __KERNEL__
#endif
#ifndef MODULE
#  define MODULE
#endif
//#include <string.h>
//#include <stdio.h>
#include <linux/proc_fs.h>
#include <linux/workqueue.h>
#include <linux/sched.h>
#include <linux/delay.h> 
#include <asm/uaccess.h>

#include <linux/module.h>
#include <linux/init.h>
#include <linux/moduleparam.h>

#include <linux/sched.h>
#include <linux/kernel.h> /* printk() */
#include <linux/slab.h> /* kmalloc() */
#include <linux/errno.h>  /* error codes */
#include <linux/types.h>  /* size_t */
#include <linux/interrupt.h> /* mark_bh */

#include <linux/in.h>
#include <linux/netdevice.h>   /* struct device, and other headers */
#include <linux/etherdevice.h> /* eth_type_trans */
#include <linux/ip.h>          /* struct iphdr */
#include <linux/tcp.h>         /* struct tcphdr */
#include <linux/skbuff.h>

#include "snull.h"

#include <linux/in6.h>
#include <asm/checksum.h>
//wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic hello.c M=/home/wonder/layer modules
MODULE_LICENSE("GPL");
#define MODULE_VERS "1.0"
#define MODULE_NAME "procfs_example"
#define FOOBAR_LEN 8
struct fb_data_t {
    char name[FOOBAR_LEN + 1];
    char value[FOOBAR_LEN + 1];
};

static struct proc_dir_entry *example_dir, *bar_file, *symlink;
struct fb_data_t bar_data;
struct workqueue_struct *test_wq;
struct delayed_work test_dwq;

char *hello_str = "Hello, world!\n";
 
void delay_func(struct work_struct *work);

static struct tasklet_struct my_tasklet ;  
static void tasklet_handler(unsigned long data)
{
        printk(KERN_ALERT "3333tasklet_handler is running./n");
    //tasklet_schedule(&my_tasklet);
}

/*
 * Transmitter lockup simulation, normally disabled.
 */
static int lockup = 0;
module_param(lockup, int, 0);

static int timeout = SNULL_TIMEOUT;
module_param(timeout, int, 0);

/*
 * Do we run in NAPI mode?
 */
static int use_napi = 0;
module_param(use_napi, int, 0);

struct net_device *snull_devs[1];
/*
 * A structure representing an in-flight packet.
 */
struct snull_packet {
    struct snull_packet *next;
    struct net_device *dev;
    int    datalen;
    u8 data[ETH_DATA_LEN];
};

int pool_size = 8;
module_param(pool_size, int, 0);

/*
 * This structure is private to each device. It is used to pass
 * packets in and out, so there is place for a packet
 */

struct snull_priv {
    struct net_device_stats stats;
    int status;
    struct snull_packet *ppool;
    struct snull_packet *rx_queue;  /* List of incoming packets */
    int rx_int_enabled;
    int tx_packetlen;
    u8 *tx_packetdata;
    struct sk_buff *skb;
    spinlock_t lock;
    struct net_device *dev;
    struct napi_struct napi;
  /* Consider creating new struct for snull device, and putting
   *  the struct net_dev in here.
   */
};

static void snull_tx_timeout(struct net_device *dev);
static void (*snull_interrupt)(int, void *, struct pt_regs *);

/*
 * Set up a device's packet pool.
 */
void snull_setup_pool(struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);
    int i;
    struct snull_packet *pkt;

    priv->ppool = NULL;
    for (i = 0; i < pool_size; i++) {
        pkt = kmalloc (sizeof (struct snull_packet), GFP_KERNEL);
        if (pkt == NULL) {
            printk (KERN_NOTICE "Ran out of memory allocating packet pool\n");
            return;
        }
        pkt->dev = dev;
        pkt->next = priv->ppool;
        priv->ppool = pkt;
    }
}

void snull_teardown_pool(struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);
    struct snull_packet *pkt;
    
    while ((pkt = priv->ppool)) {
        priv->ppool = pkt->next;
        kfree (pkt);
        /* FIXME - in-flight packets ? */
    }
}    

/*
 * Buffer/pool management.
 */
struct snull_packet *snull_get_tx_buffer(struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);
    unsigned long flags;
    struct snull_packet *pkt;
    
    spin_lock_irqsave(&priv->lock, flags);
    pkt = priv->ppool;
    priv->ppool = pkt->next;
    if (priv->ppool == NULL) {
        printk (KERN_INFO "Pool empty\n");
        netif_stop_queue(dev);
    }
    spin_unlock_irqrestore(&priv->lock, flags);
    return pkt;
}


void snull_release_buffer(struct snull_packet *pkt)
{
    unsigned long flags;
    struct snull_priv *priv = netdev_priv(pkt->dev);
    
    spin_lock_irqsave(&priv->lock, flags);
    pkt->next = priv->ppool;
    priv->ppool = pkt;
    spin_unlock_irqrestore(&priv->lock, flags);
    if (netif_queue_stopped(pkt->dev) && pkt->next == NULL)
        netif_wake_queue(pkt->dev);
}

void snull_enqueue_buf(struct net_device *dev, struct snull_packet *pkt)
{
    unsigned long flags;
    struct snull_priv *priv = netdev_priv(dev);

    spin_lock_irqsave(&priv->lock, flags);
    pkt->next = priv->rx_queue;  /* FIXME - misorders packets */
    priv->rx_queue = pkt;
    spin_unlock_irqrestore(&priv->lock, flags);
}

struct snull_packet *snull_dequeue_buf(struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);
    struct snull_packet *pkt;
    unsigned long flags;

    spin_lock_irqsave(&priv->lock, flags);
    pkt = priv->rx_queue;
    if (pkt != NULL)
        priv->rx_queue = pkt->next;
    spin_unlock_irqrestore(&priv->lock, flags);
    return pkt;
}

/*
 * Enable and disable receive interrupts.
 */
static void snull_rx_ints(struct net_device *dev, int enable)
{
    struct snull_priv *priv = netdev_priv(dev);
    priv->rx_int_enabled = enable;
}

    
/*
 * Open and close
 */

int snull_open(struct net_device *dev)
{
    /* request_region(), request_irq(), ....  (like fops->open) */

    /* 
     * Assign the hardware address of the board: use "\0SNULx", where
     * x is 0 or 1. The first byte is '\0' to avoid being a multicast
     * address (the first byte of multicast addrs is odd).
     */
    //memcpy(dev->dev_addr, "\0SNUL0", ETH_ALEN);
    //if (dev == snull_devs[1])
        //dev->dev_addr[ETH_ALEN-1]++; /* \0SNUL1 */
    netif_start_queue(dev);
    return 0;
}

int snull_release(struct net_device *dev)
{
    /* release ports, irq and such -- like fops->close */

    netif_stop_queue(dev); /* can't transmit any more */
    return 0;
}

/*
 * Configuration changes (passed on by ifconfig)
 */
int snull_config(struct net_device *dev, struct ifmap *map)
{
    if (dev->flags & IFF_UP) /* can't act on a running interface */
        return -EBUSY;

    /* Don't allow changing the I/O address */
    if (map->base_addr != dev->base_addr) {
        printk(KERN_WARNING "snull: Can't change I/O address\n");
        return -EOPNOTSUPP;
    }

    /* Allow changing the IRQ */
    if (map->irq != dev->irq) {
        dev->irq = map->irq;
            /* request_irq() is delayed to open-time */
    }

    /* ignore other fields */
    return 0;
}

/*
 * Receive a packet: retrieve, encapsulate and pass over to upper levels
 */
void snull_rx(struct net_device *dev, struct snull_packet *pkt)
{
    struct sk_buff *skb;
    struct snull_priv *priv = netdev_priv(dev);

    /*
     * The packet has been retrieved from the transmission
     * medium. Build an skb around it, so upper layers can handle it
     */
    skb = dev_alloc_skb(pkt->datalen + 2);
    if (!skb) {
        if (printk_ratelimit())
            printk(KERN_NOTICE "snull rx: low on mem - packet dropped\n");
        priv->stats.rx_dropped++;
        goto out;
    }
    skb_reserve(skb, 2); /* align IP on 16B boundary */  
    memcpy(skb_put(skb, pkt->datalen), pkt->data, pkt->datalen);

    /* Write metadata, and then pass to the receive level */
    skb->dev = dev;
    skb->protocol = eth_type_trans(skb, dev);
    skb->ip_summed = CHECKSUM_UNNECESSARY; /* don't check it */
    priv->stats.rx_packets++;
    priv->stats.rx_bytes += pkt->datalen;
    netif_rx(skb);
  out:
    return;
}    
/*
 * Transmit a packet (low level interface)
 */
static void snull_hw_tx(char *buf, int len, struct net_device *dev)
{
    /*
     * This function deals with hw details. This interface loops
     * back the packet to the other snull interface (if any).
     * In other words, this function implements the snull behaviour,
     * while all other procedures are rather device-independent
     */
    struct iphdr *ih;
    struct net_device *dest;
    struct snull_priv *priv;
    u32 *saddr, *daddr;
    struct snull_packet *tx_buffer;
    
    /* I am paranoid. Ain't I? */
    if (len < sizeof(struct ethhdr) + sizeof(struct iphdr)) {
        printk("snull: Hmm... packet too short (%i octets)\n",
                len);
        return;
    }

    if (0) { /* enable this conditional to look at the data */
        int i;
        PDEBUG("len is %i\n" KERN_DEBUG "data:",len);
        for (i=14 ; i<len; i++)
            printk(" %02x",buf[i]&0xff);
        printk("\n");
    }
    /*
     * Ethhdr is 14 bytes, but the kernel arranges for iphdr
     * to be aligned (i.e., ethhdr is unaligned)
     */
    ih = (struct iphdr *)(buf+sizeof(struct ethhdr));
    saddr = &ih->saddr;
    daddr = &ih->daddr;

    ((u8 *)saddr)[2] ^= 1; /* change the third octet (class C) */
    ((u8 *)daddr)[2] ^= 1;

    ih->check = 0;         /* and rebuild the checksum (ip needs it) */
    ih->check = ip_fast_csum((unsigned char *)ih,ih->ihl);

    if (dev == snull_devs[0])
        PDEBUGG("%08x:%05i --> %08x:%05i\n",
                ntohl(ih->saddr),ntohs(((struct tcphdr *)(ih+1))->source),
                ntohl(ih->daddr),ntohs(((struct tcphdr *)(ih+1))->dest));
    else
        PDEBUGG("%08x:%05i <-- %08x:%05i\n",
                ntohl(ih->daddr),ntohs(((struct tcphdr *)(ih+1))->dest),
                ntohl(ih->saddr),ntohs(((struct tcphdr *)(ih+1))->source));

    /*
     * Ok, now the packet is ready for transmission: first simulate a
     * receive interrupt on the twin device, then  a
     * transmission-done on the transmitting device
     */
    dest = snull_devs[dev == snull_devs[0] ? 1 : 0];
    priv = netdev_priv(dest);
    tx_buffer = snull_get_tx_buffer(dev);
    tx_buffer->datalen = len;
    memcpy(tx_buffer->data, buf, len);
    snull_enqueue_buf(dest, tx_buffer);
    if (priv->rx_int_enabled) {
        priv->status |= SNULL_RX_INTR;
        snull_interrupt(0, dest, NULL);
    }

    priv = netdev_priv(dev);
    priv->tx_packetlen = len;
    priv->tx_packetdata = buf;
    priv->status |= SNULL_TX_INTR;
    if (lockup && ((priv->stats.tx_packets + 1) % lockup) == 0) {
            /* Simulate a dropped transmit interrupt */
        netif_stop_queue(dev);
        PDEBUG("Simulate lockup at %ld, txp %ld\n", jiffies,
                (unsigned long) priv->stats.tx_packets);
    }
    else
        snull_interrupt(0, dev, NULL);
}

/*
 * Transmit a packet (called by the kernel)
 */
int snull_tx(struct sk_buff *skb, struct net_device *dev)
{
    int len;
    char *data, shortpkt[ETH_ZLEN];
    struct snull_priv *priv = netdev_priv(dev);
    
    data = skb->data;
    len = skb->len;
    if (len < ETH_ZLEN) {
        memset(shortpkt, 0, ETH_ZLEN);
        memcpy(shortpkt, skb->data, skb->len);
        len = ETH_ZLEN;
        data = shortpkt;
    }
    dev->trans_start = jiffies; /* save the timestamp */

    /* Remember the skb, so we can free it at interrupt time */
    priv->skb = skb;

    /* actual deliver of data is device-specific, and not shown here */
    snull_hw_tx(data, len, dev);

    return 0; /* Our simple device can not fail */
}

/*
 * Deal with a transmit timeout.
 */
void snull_tx_timeout (struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);

    PDEBUG("Transmit timeout at %ld, latency %ld\n", jiffies,
            jiffies - dev->trans_start);
        /* Simulate a transmission interrupt to get things moving */
    priv->status = SNULL_TX_INTR;
    snull_interrupt(0, dev, NULL);
    priv->stats.tx_errors++;
    netif_wake_queue(dev);
    return;
}



/*
 * Ioctl commands 
 */
int snull_ioctl(struct net_device *dev, struct ifreq *rq, int cmd)
{
    PDEBUG("ioctl\n");
    return 0;
}

/*
 * Return statistics to the caller
 */
struct net_device_stats *snull_stats(struct net_device *dev)
{
    struct snull_priv *priv = netdev_priv(dev);
    return &priv->stats;
}

/*
 * This function is called to fill up an eth header, since arp is not
 * available on the interface
 */
int snull_rebuild_header(struct sk_buff *skb)
{
    struct ethhdr *eth = (struct ethhdr *) skb->data;
    struct net_device *dev = skb->dev;
    
    memcpy(eth->h_source, dev->dev_addr, dev->addr_len);
    memcpy(eth->h_dest, dev->dev_addr, dev->addr_len);
    eth->h_dest[ETH_ALEN-1]   ^= 0x01;   /* dest is us xor 1 */
    return 0;
}


int snull_header(struct sk_buff *skb, struct net_device *dev,
         unsigned short type, const void *daddr, const void *saddr,
                unsigned int len)
{
    struct ethhdr *eth = (struct ethhdr *)skb_push(skb,ETH_HLEN);

    eth->h_proto = htons(type);
    memcpy(eth->h_source, saddr ? saddr : dev->dev_addr, dev->addr_len);
    memcpy(eth->h_dest,   daddr ? daddr : dev->dev_addr, dev->addr_len);
    eth->h_dest[ETH_ALEN-1]   ^= 0x01;   /* dest is us xor 1 */
    return (dev->hard_header_len);
}





/*
 * The "change_mtu" method is usually not needed.
 * If you need it, it must be like this.
 */
int snull_change_mtu(struct net_device *dev, int new_mtu)
{
    unsigned long flags;
    struct snull_priv *priv = netdev_priv(dev);
    spinlock_t *lock = &priv->lock;
    
    /* check ranges */
    if ((new_mtu < 68) || (new_mtu > 1500))
        return -EINVAL;
    /*
     * Do anything you need, and the accept the value
     */
    spin_lock_irqsave(lock, flags);
    dev->mtu = new_mtu;
    spin_unlock_irqrestore(lock, flags);
    return 0; /* success */
}

static const struct header_ops snull_header_ops = {
    .create     = snull_header,
    .rebuild = snull_rebuild_header,
    .cache     = NULL,  /* disable caching */
};




/*
 * Finally, the module stuff
 */

void snull_cleanup(void)
{
    int i;
    
    for (i = 0; i < 2;  i++) {
        if (snull_devs[i]) {
            unregister_netdev(snull_devs[i]);
            snull_teardown_pool(snull_devs[i]);
            free_netdev(snull_devs[i]);
        }
    }
    return;
}


  
void delay_func(struct work_struct *work)
{
    //int i;
 
    printk(KERN_INFO "My name is delay_func!\n");
    //int ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //for (i = 0; i < 3; i++) {
        //printk(KERN_ERR "delay_fun:i=%d\n", i);
        //msleep(1000);
    //}
} 
static int
hello_read_proc(char *buffer, char **start, off_t offset, int size, int *eof, void *data)
{
        
        //char*hello_str = buffer;
        int len = strlen(hello_str); /* Don't include the null byte. */
        /*
         * We only support reading the whole string at once.
         */
        if(size < len)
           return -EINVAL;
        /*
         * If file position is non-zero, then assume the string has
         * been read and indicate there is no more data to be read.
         */
        if (offset != 0)
           return 0;
        /*
         * We know the buffer is big enough to hold the string.
         */
        strcpy(buffer, hello_str);
        /*
         * Signal EOF.
         */
        *eof = 1;

        return len;
}
char *strcat2(char *dst, char *src)
{
    char * cp = dst;
    while( *cp )
    cp++; /* find end of dst */

    while( *cp++ = *src++ ) ; /* Copy src to end of dst */

    return( dst ); /* return dst */
}
static int __init hello_init(void)
{
    int rv = 0;

    //struct net_device *ethdev;
    dev_get_by_name(snull_devs[0], "eth0");

    if (snull_devs[0] == NULL)
      return 0;

    struct sk_buff *databuffer;
    databuffer = dev_alloc_skb(12 + 2);//dev_alloc_skb(pkt->datalen + 2);
    skb_reserve(databuffer, 2); /* align IP on 16B boundary */  
    memcpy(skb_put(databuffer, 12), "data here", 12);//memcpy(skb_put(skb, 12), pkt->data, pkt->datalen)
    databuffer->dev = snull_devs[0];
    databuffer->protocol = eth_type_trans(databuffer, snull_devs[0]);
    databuffer->ip_summed = CHECKSUM_UNNECESSARY; /* don't check it */
    //netif_receive_skb(skb);

    int tx_ret = snull_tx(databuffer, snull_devs[0]);

    //if (create_proc_read_entry("hello_world", 0, NULL, hello_read_proc, NULL) == 0) {
        //printk(KERN_ERR
               //"Unable to register \"Hello, world!\" proc file\n");
        //return -ENOMEM;
    //}
    hello_str = "Step0\n";
    //msleep(10000);
    char* hello_str1 = "Step0 ";
    char* hello_str2 = "Step1 ";
    //hello_str = strcat2(hello_str1, hello_str2);
    //msleep(10000);
    hello_str2 = "Step2 ";
    //hello_str = strcat2(hello_str1, hello_str2);
    //msleep(10000);
    //remove_proc_entry("hello_world", NULL);

    tasklet_init(&my_tasklet, tasklet_handler, 0);
    tasklet_schedule(&my_tasklet);

    /* create symlink */
    //symlink = proc_symlink("jiffies_too", example_dir,"jiffies");
    //if(symlink == NULL) {
       //rv = -ENOMEM;
       //goto no_symlink;
    //}
    //symlink->owner = THIS_MODULE;
    //int i;
    //int ret;
 
    //test_wq = create_workqueue("test_wq");
    //if (!test_wq) {
        //printk(KERN_ERR "No memory for workqueue\n");
        //return 1;    
    //}
    //printk(KERN_INFO "Create Workqueue successful!\n");
 
    //INIT_DELAYED_WORK(&test_dwq, delay_func);
     
    //ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //printk(KERN_INFO "444 first ret=%d!\n", ret);
    
    //for (i = 0; i <= 100; i++) {  
    //if(i==100)
    //{
            //printk(KERN_INFO "Example:ret= %d,i=%d\n", ret, i);
    //}
        //msleep(100);
    //}
 
    //ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //printk(KERN_INFO "444 second ret=%d!\n", ret);
 
    return 0;
}
static void __exit hello_exit(void)
{
  tasklet_kill (&my_tasklet);
  remove_proc_entry("hello_world", NULL);
  //int ret;
  //ret = cancel_delayed_work(&test_dwq);
  //flush_workqueue(test_wq);
  //destroy_workqueue(test_wq);
  //printk(KERN_INFO "Goodday! ret=%d\n", ret); 
  printk("Unloading hello.\n");
  return;
}

module_init(hello_init);
module_exit(hello_exit);

```

```

#include <sys/mman.h>
#include <sys/socket.h>
#include <linux/if_packet.h>
#include <linux/if_ether.h>
#include <linux/if_arp.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <netinet/in.h>
#include <ctype.h>
#include <unistd.h>
//#define ETH_FRAME_LEN 1518
// 14 + 46-1500 + 4
#define ETH_FRAME_LEN 64
char *trimwhitespace(char *str)
{
  char *end;

  // Trim leading space
  while(isspace(*str)) str++;

  if(*str == 0)  // All spaces?
    return str;

  // Trim trailing space
  end = str + strlen(str) - 1;
  while(end > str && isspace(*end)) end--;

  // Write new null terminator
  *(end+1) = 0;

  return str;
}
char *replace_str(char *str, char *orig, char *rep)
{
  static char buffer[4096];
  char *p;

  if(!(p = strstr(str, orig)))  // Is 'orig' even in 'str'?
    return str;

  strncpy(buffer, str, p-str); // Copy characters from 'str' start to 'orig' st$
  buffer[p-str] = '\0';

  sprintf(buffer+(p-str), "%s%s", rep, p+strlen(orig));

  return buffer;
}
int main()
{
int s; /*socketdescriptor*/

s = socket(AF_PACKET, SOCK_RAW, htons(ETH_P_ALL));
if (s == -1) { printf("socket error"); }
/*
tpacket_req req;
req.tp_block_size=96;
req.tp_frame_size=96;
req.tp_block_nr=1;
req.tp_frame_nr=(req.tp_block_size / req.tp_frame_size) * req.tp_block_nr;
if ( (setsockopt(s,
    SOL_PACKET,
    PACKET_RX_RING,
    (char *)&req,
    sizeof(req))) != 0 ) {
    perror("setsockopt()");
    close(s);
    return 1;
};
char* map=(char*)mmap(NULL, req.tp_block_size * req.tp_block_nr, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_SHARED, s, 0);
*/

/*target address*/
struct sockaddr_ll socket_address;

/*buffer for ethernet frame*/
unsigned char* buffer = (unsigned char*)malloc(ETH_FRAME_LEN);

/*pointer to ethenet header*/
unsigned char* etherhead = (unsigned char*)buffer;
    
/*userdata in ethernet frame*/
unsigned char* data = (unsigned char*)(buffer);
    
/*another pointer to ethernet header*/
struct ethhdr *eh = (struct ethhdr *)etherhead;
 
int send_result = 0;

/*our MAC address*/
unsigned char src_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};

/*other host MAC address 10:78:d2:ad:90:cb*/
unsigned char dest_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};

/*prepare sockaddr_ll*/

/*RAW communication*/
socket_address.sll_family   = PF_PACKET;    
/*we don't use a protocoll above ethernet layer
  ->just use anything here*/
socket_address.sll_protocol = htons(ETH_P_IP);    

/*index of the network device
see full code later how to retrieve it*/
socket_address.sll_ifindex  = 2;

/*ARP hardware identifier is ethernet*/
socket_address.sll_hatype   = ARPHRD_ETHER;
    
/*target is another host*/
socket_address.sll_pkttype  = PACKET_OTHERHOST;

/*address length*/
socket_address.sll_halen    = ETH_ALEN;        
/*MAC - begin*/
socket_address.sll_addr[0]  = 0x10;        
socket_address.sll_addr[1]  = 0x78;        
socket_address.sll_addr[2]  = 0xd2;
socket_address.sll_addr[3]  = 0xad;
socket_address.sll_addr[4]  = 0x90;
socket_address.sll_addr[5]  = 0xcb;
/*MAC - end*/
socket_address.sll_addr[6]  = 0x00;/*not used*/
socket_address.sll_addr[7]  = 0x00;/*not used*/

int length=0;
int succeed = 0;
int i =0;
int j = 0;
while(true)
{
    length = recvfrom(s, buffer, ETH_FRAME_LEN, 0, NULL, NULL);

    if (length == -1 && succeed == 0) {
        printf("recv error\n");
        succeed = 2;
    }
    if(length > 0)
    {
        char buff[4] = "\0";
        memcpy(&buff, &buffer[14], 4);
        //printf(trimwhitespace(buff));
        printf(buff);
    }
}
}



```

---

