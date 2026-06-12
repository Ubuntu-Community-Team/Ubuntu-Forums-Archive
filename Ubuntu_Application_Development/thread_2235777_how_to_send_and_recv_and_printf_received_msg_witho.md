---
title: "how to send and recv and printf received msg without running tcpdump"
date: 2014-07-22
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-07-22
[COLOR=#000000]this program can only show received message when[/COLOR]
[COLOR=#000000]tcpdump eth0 in another console[/COLOR]

[COLOR=#000000]when tcpdump running, it will show extra character E, even if char[3] and memcpy(&a,&b[14], 3)[/COLOR]

[COLOR=#000000]why it can not show received message without running tcpdump?[/COLOR]

[COLOR=#000000]which is missing ?[/COLOR]


[COLOR=#000000]i guess the buffer in somewhere is not full, so that it stop at somewhere and tcpdump help to flush this buffer[/COLOR]
[COLOR=#000000]so that it can show received msg when running tcp dump[/COLOR]

[COLOR=#000000]then i guess that i have to set mmap[/COLOR]

[COLOR=#000000]both client and server i added code below , just different in [/COLOR]
[COLOR=#000000]PACKET_TX_RING and [/COLOR]
[COLOR=#000000]PACKET_RX_RING and use DONTWAIT when sendto[/COLOR]

[COLOR=#000000]but it return compile error, socket invalid option[/COLOR]

```

[COLOR=#000000]//96/96 = 1, 1*1 = 1[/COLOR]
[COLOR=#000000]tpacket_req req;[/COLOR]
[COLOR=#000000]req.tp_block_size=96;[/COLOR]
[COLOR=#000000]req.tp_frame_size=96;[/COLOR]
[COLOR=#000000]req.tp_block_nr=1;[/COLOR]
[COLOR=#000000]req.tp_frame_nr=(req.tp_block_size / req.tp_frame_size) * req.tp_block_nr;[/COLOR]
[COLOR=#000000]if ( (setsockopt(s,[/COLOR]
[COLOR=#000000]SOL_PACKET,[/COLOR]
[COLOR=#000000]PACKET_TX_RING,[/COLOR]
[COLOR=#000000](char *)&req,[/COLOR]
[COLOR=#000000]sizeof(req))) != 0 ) {[/COLOR]
[COLOR=#000000]perror("setsockopt()");[/COLOR]
[COLOR=#000000]close(s);[/COLOR]
[COLOR=#000000]return 1;[/COLOR]
[COLOR=#000000]};[/COLOR]
[COLOR=#000000]char* map=(char*)mmap(NULL, req.tp_block_size * req.tp_block_nr, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_SHARED, s, 0);[/COLOR]

```


```

[COLOR=#000000]#include <sys/socket.h>[/COLOR]
[COLOR=#000000]#include <linux/if_packet.h>[/COLOR]
[COLOR=#000000]#include <linux/if_ether.h>[/COLOR]
[COLOR=#000000]#include <linux/if_arp.h>[/COLOR]
[COLOR=#000000]#include <stdio.h>[/COLOR]
[COLOR=#000000]#include <stdlib.h>[/COLOR]
[COLOR=#000000]#include <string.h>[/COLOR]
[COLOR=#000000]#include <netinet/in.h>[/COLOR]
[COLOR=#000000]#include <ctype.h>[/COLOR]
[COLOR=#000000]//#define ETH_FRAME_LEN 1518[/COLOR]
[COLOR=#000000]// 14 + 46-1500 + 4[/COLOR]
[COLOR=#000000]#define ETH_FRAME_LEN 60[/COLOR]
[COLOR=#000000]char *trimwhitespace(char *str)[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]char *end;[/COLOR]

[COLOR=#000000]// Trim leading space[/COLOR]
[COLOR=#000000]while(isspace(*str)) str++;[/COLOR]

[COLOR=#000000]if(*str == 0) // All spaces?[/COLOR]
[COLOR=#000000]return str;[/COLOR]

[COLOR=#000000]// Trim trailing space[/COLOR]
[COLOR=#000000]end = str + strlen(str) - 1;[/COLOR]
[COLOR=#000000]while(end > str && isspace(*end)) end--;[/COLOR]

[COLOR=#000000]// Write new null terminator[/COLOR]
[COLOR=#000000]*(end+1) = 0;[/COLOR]

[COLOR=#000000]return str;[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]char *replace_str(char *str, char *orig, char *rep)[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]static char buffer[4096];[/COLOR]
[COLOR=#000000]char *p;[/COLOR]

[COLOR=#000000]if(!(p = strstr(str, orig))) // Is 'orig' even in 'str'?[/COLOR]
[COLOR=#000000]return str;[/COLOR]

[COLOR=#000000]strncpy(buffer, str, p-str); // Copy characters from 'str' start to 'orig' st$[/COLOR]
[COLOR=#000000]buffer[p-str] = '\0';[/COLOR]

[COLOR=#000000]sprintf(buffer+(p-str), "%s%s", rep, p+strlen(orig));[/COLOR]

[COLOR=#000000]return buffer;[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]int main()[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]int s; /*socketdescriptor*/[/COLOR]

[COLOR=#000000]s = socket(AF_PACKET, SOCK_RAW, htons(ETH_P_ALL));[/COLOR]
[COLOR=#000000]if (s == -1) { printf("socket error"); }[/COLOR]

[COLOR=#000000]/*target address*/[/COLOR]
[COLOR=#000000]struct sockaddr_ll socket_address;[/COLOR]

[COLOR=#000000]/*buffer for ethernet frame*/[/COLOR]
[COLOR=#000000]unsigned char* buffer = (unsigned char*)malloc(ETH_FRAME_LEN);[/COLOR]

[COLOR=#000000]/*pointer to ethenet header*/[/COLOR]
[COLOR=#000000]unsigned char* etherhead = (unsigned char*)buffer;[/COLOR]

[COLOR=#000000]/*userdata in ethernet frame*/[/COLOR]
[COLOR=#000000]unsigned char* data = (unsigned char*)(buffer);[/COLOR]

[COLOR=#000000]/*another pointer to ethernet header*/[/COLOR]
[COLOR=#000000]struct ethhdr *eh = (struct ethhdr *)etherhead;[/COLOR]

[COLOR=#000000]int send_result = 0;[/COLOR]

[COLOR=#000000]/*our MAC address*/[/COLOR]
[COLOR=#000000]unsigned char src_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};[/COLOR]

[COLOR=#000000]/*other host MAC address 10:78:d2:ad:90:cb*/[/COLOR]
[COLOR=#000000]unsigned char dest_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};[/COLOR]

[COLOR=#000000]/*prepare sockaddr_ll*/[/COLOR]

[COLOR=#000000]/*RAW communication*/[/COLOR]
[COLOR=#000000]socket_address.sll_family = PF_PACKET;	[/COLOR]
[COLOR=#000000]/*we don't use a protocoll above ethernet layer[/COLOR]
[COLOR=#000000]->just use anything here*/[/COLOR]
[COLOR=#000000]socket_address.sll_protocol = htons(ETH_P_IP);	[/COLOR]

[COLOR=#000000]/*index of the network device[/COLOR]
[COLOR=#000000]see full code later how to retrieve it*/[/COLOR]
[COLOR=#000000]socket_address.sll_ifindex = 2;[/COLOR]

[COLOR=#000000]/*ARP hardware identifier is ethernet*/[/COLOR]
[COLOR=#000000]socket_address.sll_hatype = ARPHRD_ETHER;[/COLOR]

[COLOR=#000000]/*target is another host*/[/COLOR]
[COLOR=#000000]socket_address.sll_pkttype = PACKET_OTHERHOST;[/COLOR]

[COLOR=#000000]/*address length*/[/COLOR]
[COLOR=#000000]socket_address.sll_halen = ETH_ALEN;	[/COLOR]
[COLOR=#000000]/*MAC - begin*/[/COLOR]
[COLOR=#000000]socket_address.sll_addr[0] = 0x10;	[/COLOR]
[COLOR=#000000]socket_address.sll_addr[1] = 0x78;	[/COLOR]
[COLOR=#000000]socket_address.sll_addr[2] = 0xd2;[/COLOR]
[COLOR=#000000]socket_address.sll_addr[3] = 0xad;[/COLOR]
[COLOR=#000000]socket_address.sll_addr[4] = 0x90;[/COLOR]
[COLOR=#000000]socket_address.sll_addr[5] = 0xcb;[/COLOR]
[COLOR=#000000]/*MAC - end*/[/COLOR]
[COLOR=#000000]socket_address.sll_addr[6] = 0x00;/*not used*/[/COLOR]
[COLOR=#000000]socket_address.sll_addr[7] = 0x00;/*not used*/[/COLOR]

[COLOR=#000000]int length=0;[/COLOR]
[COLOR=#000000]int succeed = 0;[/COLOR]
[COLOR=#000000]int i =0;[/COLOR]
[COLOR=#000000]int j = 0;[/COLOR]
[COLOR=#000000]while(true)[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]length = recvfrom(s, buffer, ETH_FRAME_LEN, 0, NULL, NULL);[/COLOR]

[COLOR=#000000]if (length == -1 && succeed == 0) {[/COLOR]
[COLOR=#000000]printf("recv error\n");[/COLOR]
[COLOR=#000000]succeed = 2;[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]if(length > 0)[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]char buff[46] = "\0";[/COLOR]
[COLOR=#000000]memcpy(&buff, &buffer[14], 46);[/COLOR]
[COLOR=#000000]printf(trimwhitespace(buff));[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]}

```[/COLOR]

---

