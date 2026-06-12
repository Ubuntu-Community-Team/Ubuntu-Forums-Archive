---
title: "&quot;resource temporarily unavailable&quot; in recv in socket programming"
date: 2013-02-12
forum: Ubuntu Application Development
---

### Post by mrjmrj on 2013-02-12
I want to read and write over Wanpipe driver (a network device driver for Sangoma cards) via socket programming but i get this message error: "resource temporarily unavailable". The card is working and i see it send and receive packets in ifconfig. I have included my code and would be very pleased if somebody help me in this. 
A related question: I set the socket to blocking mode but the recv message does not block? how could i block the recv?

int main(void)
{
	int sd;
	int buflen=WP_HEADER + MAX_PACKET;
	char buf[buflen];
	struct wan_sockaddr_ll sa;
	sd = socket(AF_WANPIPE, SOCK_RAW,0);
	if (sd < 0) /* if socket failed to initialize, exit */
    {
      perror("Error Creating Socket");
      exit(1);
    }
	printf("Socket Descriptor:%d\n",sd);
	memset(&sa,0,sizeof(struct wan_sockaddr_ll));
	
		strncpy((char*)sa.sll_card,"wanpipe1",sizeof(sa.sll_card));
    strncpy((char*)sa.sll_device,"w1g1",sizeof(sa.sll_device));	
	sa.sll_protocol = htons(PVC_PROT);
    sa.sll_family = AF_WANPIPE;

	if(bind(sd, (struct sockaddr *)&sa, sizeof(sa)) < 0)
    {
      perror("error bind failed");
      close(sd);
      exit(1);
    }
	
	
	int data=0;
	int ret=ioctl(sd,FIONBIO,&data);
	if (ret < 0) {
            perror("ioctl error!");
			close(sd);
            return 1;
    }

	fd_set read_fds;
	struct timeval timeout;
	timeout.tv_sec = 10;
	timeout.tv_usec = 0;
	FD_ZERO(&read_fds);
	FD_SET(sd,&read_fds);
	if(select(sd+1, &read_fds, NULL, NULL, &timeout) < 0)
	{
		perror("select() error!");
		exit(1);
	}

	if (FD_ISSET(sd,&read_fds))
		printf("There is data for reading\n");
	else
		printf("There is no data for reading\n");*/
	
	// MSG_WAITALL | MSG_PEEK | MSG_OOB
	int r=recv(sd,buf,buflen,0);
	if (r < 0) {
            perror("Wanpipe raw socket reading");
			close(sd);
            exit(1);
    }
	printf("\nNumber of bytes read into the buffer: %d",r);
	printf("\nThe read buffer: ");
	puts(buf);
	close(sd);
}

thank you in advance.

---

