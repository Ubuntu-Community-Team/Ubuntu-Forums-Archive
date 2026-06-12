---
title: "one-to-one server VS one-to-many server"
date: 2011-02-18
forum: Server Platforms
---

### Post by darshan123 on 2011-02-18
Hi,

I am actually writing a single SCTP server which needs to handle  thousands of clients pumping msgs at various rates. I am thinking of below options to make the server multi-threaded. Please  provide some inputs.  

1. Make SCTP server socket a one-to-many styled (SOCK_SEQPACKET). Since  all clients connect to same socket, I can remove the overhead of  select/epoll and I can have multiple threads to read from the same  global socket. Actually can different threads read from the same socket ?  (No syncronization in sctp_recvmsg() ?)  

2. Make SCTP server socket a one-to-one styled, where the accept returns  individual sockets to be read for each client. If I choose to  multithread the server, then creating 1000 threads for 1000 clients is  not feasible. So I should have a thread pool where each thread handles a  bundle of client fds. But is this not a bad design when it comes to  performance? Isn't the former approach better one ?  

But I read that a one-to-one server is always a better and used  everywhere. But logically for me it looks like a one-to-many server best  suites my requirement.  Please enlighten me.  

Thanks, 
Darshan

---

