---
title: "Contacting the SSH daemon with telnet?"
date: 2018-02-17
forum: Server Platforms
---

### Post by nandi.debian on 2018-02-17
I don't understand the meaning of this: **"try connecting to the ssh daemon on your linux machine with telnet(1)"**, it supposed to give some special or curious answer.

When I tried to connect on putty chosing telnet and port 23 I get the message "network error: connection refused" becuase telnet server offcourse is not included on my linux newer version for security reasons, I then install telnet server and I could login via putty, but off course not encrypted. Neither of that told me anything of a special or curious sort like I was told.:confused:

I also tried $telnet sshd and various of such nature.

---

### Post by TheFu on 2018-02-17
Seems like bad advice.
Some people don't understand that "terminal" is separate from the protocol used for remote connections. Could that be the issue for the person providing the advice?

---

### Post by steeldriver on 2018-02-17
... the "special or curious answer" *when you connect to the SSH port* is really just a version string from the SSH server:

```

$ telnet localhost 22
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
^]
telnet>

```

---

### Post by nandi.debian on 2018-02-17
> **steeldriver said:**
> ... the "special or curious answer" *when you connect to the SSH port* is really just a version string from the SSH server:

```

$ telnet localhost 22
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
^]
telnet>

```

Yes I have done such as well, but i's as you say not "special or curious"....the person also said use 'quit' to get out of it, which sounds like there would be loads of data. Really mysterious.

---

### Post by nandi.debian on 2018-02-17
> **TheFu said:**
> Seems like bad advice.
Some people don't understand that "terminal" is separate from the protocol used for remote connections. Could that be the issue for the person providing the advice?

Yes, telnet (server) is unsafe, it's not really advice, more like a "riddle", not sure if they meant terminal or ssh client. I have tried both procedures.

---

### Post by steeldriver on 2018-02-17
> **nandi.debian said:**
> Yes I have done such as well, but i's as you say not "special or curious"....the person also said use 'quit' to get out of it, which sounds like there would be loads of data. Really mysterious.

They probably just meant to type `quit` at the `telnet>` prompt to close the session (CTRL-D should also work)

---

### Post by HermanAB on 2018-02-17
Telnet is a handy tool for debugging network trouble.  When you use telnet to connect to a ssh server, you should see the server version string.  The actual connection will fail, since telnet cannot speak the ssh protocol.  However, if you don't get the version string, then you will get one of several error messages, which will give you some clue as to what is wrong with your network.  E.g. the DNS, routing, bad connections...

So, there is nothing mysterious about it.  I frequently use telnet like this.  A couple hours ago, I was trying to connect to another machine in the house and it failed, so I also ran telnet like this and eventually figured out the ssh daemon on the other need to be restarted, since its IP address changed.

---

### Post by wildmanne39 on 2018-02-17
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by nandi.debian on 2018-02-19
> **HermanAB said:**
> Telnet is a handy tool for debugging network trouble.  When you use telnet to connect to a ssh server, you should see the server version string.  The actual connection will fail, since telnet cannot speak the ssh protocol.  However, if you don't get the version string, then you will get one of several error messages, which will give you some clue as to what is wrong with your network.  E.g. the DNS, routing, bad connections...

So, there is nothing mysterious about it.  I frequently use telnet like this.  A couple hours ago, **I was trying to connect to another machine in the house and it failed, so I also ran telnet like this and eventually figured out the ssh daemon on the other need to be restarted, since its IP address changed**.

That seems like the only usage in this way. 'telnet <ip> <port>'.

---

