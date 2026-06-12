---
title: "trouble connecting to a listening service"
date: 2018-11-14
forum: Server Platforms
---

### Post by refaatmokhtar on 2018-11-14
:mad:Ubuntu 16.04 is running on a TX2. 
- running Ubuntu as a server with (nc -l 50000) works fine, I can connect to from a client (nc ip 50000) and exchange messages
- however, when running an application on the Ubuntu server, I am NOT able to connect it from the client (using nc ip 50000), wit Connection Timed Out.
- I have read in another forum ([https://support.rackspace.com/how-to/testing-network-services-with-netcat/](https://support.rackspace.com/how-to/testing-network-services-with-netcat/)), that it might be the firewall, here is the output of iptables on the Ubuntu server:
[COLOR=#000000][FONT=Menlo]Chain INPUT (policy ACCEPT)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]target     prot opt source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain FORWARD (policy ACCEPT)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]target     prot opt source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain OUTPUT (policy ACCEPT)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]target     prot opt source               destination         [/FONT][/COLOR]

- Debugging the application shows that "accept" always return NULL even if the client is trying to connect.
Please suggestions?!

---

### Post by bashiergui on 2018-11-14
Reviewing your firewall logs would show whether the firewall is preventing connection.

Are you connecting to the server from another machine on the network? Over the internet? From the same server?

---

### Post by refaatmokhtar on 2018-11-14
Tried both, from another machine on the network and from the sever itself. Both give Timed out

---

### Post by mitesh.agrwl on 2018-11-14
> - however, when running an application on the Ubuntu server, I am NOT  able to connect it from the client (using nc ip 50000), wit Connection  Timed Out.

Is application configured properly to listen/accept messages from port 50000? Please check the same, if possible, by running an script or something on the server.

---

### Post by wildmanne39 on 2018-11-14
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by refaatmokhtar on 2018-11-15
Yes, I believe it's configured correctly because simply the same service is running fine on another Linux platform with TS-2760 processor. Here is the line of ([COLOR=#000000][FONT=Menlo]netstat -an | grep "LISTEN") 
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]
tcp        0      0 0.0.0.0:50000           0.0.0.0:*               [/FONT][COLOR=#C33720][FONT=Menlo][B]LISTEN

[/B][/FONT][/COLOR]The way we initialized the socket is:
[COLOR=#0326CC][FONT=Monaco]listen_socket[/FONT][/COLOR][COLOR=#222222][FONT=Monaco] = [/FONT][/COLOR][COLOR=#222222][FONT=Monaco]_socket_[/FONT][/COLOR][COLOR=#222222][FONT=Monaco]([/FONT][/COLOR][COLOR=#222222][FONT=Monaco]_PF_INET_[/FONT][/COLOR][COLOR=#222222][FONT=Monaco], [/FONT][/COLOR][COLOR=#222222][FONT=Monaco]_SOCK_STREAM_[/FONT][/COLOR][COLOR=#222222][FONT=Monaco], protocol->[/FONT][/COLOR][COLOR=#222222][FONT=Monaco]_p_proto_[/FONT][/COLOR][COLOR=#222222][FONT=Monaco]);[/FONT][/COLOR][/COLOR]
[FONT=Monaco]_        setsockopt_([COLOR=#0326cc]listen_socket[/COLOR], _SOL_SOCKET_, _SO_REUSEADDR_, &one, [COLOR=#931a68]sizeof[/COLOR] one);[/FONT]
[FONT=Monaco]_bind_([COLOR=#0326cc]listen_socket[/COLOR], ([COLOR=#931a68]const[/COLOR] [COLOR=#006141]sockaddr[/COLOR] *) &socketaddr, [COLOR=#931a68]sizeof[/COLOR](socketaddr)
[/FONT][FONT=Monaco]options = _fcntl_([COLOR=#0326cc]listen_socket[/COLOR], _F_GETFL_);[/FONT]
[FONT=Monaco]options |= _O_NONBLOCK_;[/FONT]
[FONT=Monaco]_fcntl_([COLOR=#0326cc]listen_socket[/COLOR], _F_SETFL_, options);[/FONT]
[FONT=Monaco]_listen_([COLOR=#0326cc]listen_socket[/COLOR], 0);
[/FONT]
[FONT=Monaco]_accept_([COLOR=#0326cc]listen_socket[/COLOR], ([COLOR=#006141]sockaddr[/COLOR] *) &this_sockaddr, &size)

Now, accept() is always return NULL on ubuntu 16.04 even if there is a client trying to connect (nc localhost 50000)[/FONT]

---

