---
title: "x2go"
date: 2010-03-28
forum: The Cafe
---

### Post by jimcooncat on 2010-03-28
Could you please relate any experience you have with x2go?
[http://www.x2go.org](http://www.x2go.org)

---

### Post by wd5gnr on 2010-03-30
I have had good luck with freenx. I was anxious to try x2go as it looks much more polished. However, I keep getting an annoying error. I log in, get the session dialog and the proxy (nxproxy?) dies and that's the end. 

Very little English help for it and I haven't found anything useful about this error.

If anyone has this working (Kubuntu 9.10 64 bit here) I'd be interested in hearing about it myself.

More info:
If you click "Details" some extra messages show up but they disappear quickly. Here's what I managed to get:

Info: Proxy running in client mode with pid '12561'.
Session: Starting session at 'Mon Mar 29 23:47:51 2010'.
Info: Connecting to remote host 'localhost:30005'.
Info: Connection to remote proxy 'localhost:30005' established.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Mon Mar 29 23:47:51 2010'.
Session: Session terminated at 'Mon Mar 29 23:47:51 2010'.

More info: It actually works well from a Windows client. So I don't know if it is the Linux client or if it just doesn't like connecting from localhost. But it works GREAT from the Windows client. The only thing I noticed funny is that it installs xming and it seems to get confused with fullscreen. But you could use another X server (e.g., cygwin) or just don't do full screen.

Update: Works great on my laptop connecting back to my desktop (laptop has i386 EEEBuntu on it). So I don't know if my desktop has a problem that inhibits the client or if it just doesn't like connecting to the same machine (which is really not useful except for testing anyway). Also, the newer beta Windows client seems to work better then stable one although I couldn't get "hidden mode" to work in either case.

When you install the Windows client you need to take the sshd install. I didn't the first time and that prevents file sharing and I think printing. It was hard to find out but your shared folders wind up in ~/media/c_shared_drive_name (if you are sharing, for example, c:\shared_drive_name). Note that is not /Media but ~/media.

---

