---
title: "[SOLVED] ssh problems"
date: 2008-03-16
forum: Server Platforms
---

### Post by magicman5421 on 2008-03-16
ok so I've been messing around with setting up an ssh server and everything has gone well so far except i cant get port forwarding to work. well...it kind of works...but it doesnt. I'm using the command line to do the port forwarding with the command
```
ssh -L 5400:localhost:5400 me@my-desktop
```
That works fine and I can enter my password and I connect.
Then I go into firefox, Edit>Preferences, Advanced>Network>Settings. I set the html proxy to localhost on port 5400, i remove localhost (and 127.0.0.1 for good measure) from the "No proxy for" box, and press ok. i then try to go to google.com. I get a blank page. When i look in the terminal window that is still open, i see
```
channel 3: open failed: connect failed: Connection refused
```
as many times as I refreshed the page.
I put in AllowTcpForwarding yes in my /etc/ssh/sshd_config file by the way (and it still doesn't work).
What did I do wrong?

---

### Post by kevdog on 2008-03-17
Are you trying to setup an http proxy for firefox?

If you do you want something different -- you want to make use of Firefox's ability to use a SOCKS5 proxy with ssh able to create this type of proxy.

At command line on the client type
ssh -D 9999 -C user@server  <--- Fill in appropriate user and server info

This will establish the ssh connection with the socks5 proxy to run on local port 9999

Then with firefox you want to set up to use 
SOCKS5 proxy only (leave all other options blank) and type in 127.0.0.1 as the Socks Host and the port as 9999

You should then be able to connect with firefox using these settings.

---

### Post by magicman5421 on 2008-03-17
thank you very much it worked 1st time.

---

