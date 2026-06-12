---
title: "Custom application and using port 23 as a regular user"
date: 2008-05-16
forum: Security
---

### Post by jbysmith on 2008-05-16
This is mostly out of curiosity.. just learning how the OS security system works, etc.

I have a custom written database app with a "telnet like" front end that I use on a daily basis.  What I'd like to do is to have it run on the standard telnet port 23.  (I don't run the regular telnet daemon, just SSH for remote work) Right now, the only way I'm able to do this is to run it as root via sudo, as if I don't, the OS won't allow me to use that port.  

It's purely a convenience thing; I have a couple people that I'd like to be able to connect to it and not have to remember a port number.  

Is there a way to tell the OS to allow me to bind to port 23 as a regular user without an elevation?  (And only port 23..)  It's not a huge deal as I can just tell the server to use a port over 1024 and be done with it, but just trying to keep things simple.

Thanks

---

### Post by HalPomeranz on 2008-05-17
In general, the answer is no, all Unix-like operating systems that I'm aware of require you to have superuser privs to bind to ports below 1024.  This is a legacy from the early days, and not generally so useful anymore, but still it persists.  Some OSes I'm familiar with (e.g. Solaris) allow you to change the port number boundary for these so-called "privileged ports", but you can't selectively make individual ports below the threshold unprivileged.

You could have xinetd start the app for you (though you'd have to change the app to work with the way xinetd does I/O), which has the advantage of allowing you to have xinetd run the app as a non-privileged user once the connection has been accepted.  This is probably more secure than you starting your app with root privileges, because I'm guessing that the app doesn't currently give up root privs after it binds to port 23.

Another alternative would be to set up a port forwarding (using IP Tables or some other mechanism) to forward the incoming port 23 traffic to your app running on some unprivileged port.

---

### Post by Oldsoldier2003 on 2008-05-17
> **HalPomeranz said:**
> In general, the answer is no, all Unix-like operating systems that I'm aware of require you to have superuser privs to bind to ports below 1024.  This is a legacy from the early days, and not generally so useful anymore, but still it persists.  Some OSes I'm familiar with (e.g. Solaris) allow you to change the port number boundary for these so-called "privileged ports", but you can't selectively make individual ports below the threshold unprivileged.

You could have xinetd start the app for you (though you'd have to change the app to work with the way xinetd does I/O), which has the advantage of allowing you to have xinetd run the app as a non-privileged user once the connection has been accepted.  This is probably more secure than you starting your app with root privileges, because I'm guessing that the app doesn't currently give up root privs after it binds to port 23.

**Another alternative would be to set up a port forwarding (using IP Tables or some other mechanism) to forward the incoming port 23 traffic to your app running on some unprivileged port**.
I think that Hal hit it on the head, use a higher port then forward 23 to that port.

---

### Post by jbysmith on 2008-05-17
That all makes sense.  I'd rather not run the thing as root.  The port forwarding idea sounds pretty workable; give me the end result I was looking for without actually taking a shortcut around the security system.

Thanks everyone.

---

### Post by jklm988 on 2008-05-19
Agree with your view, to support you[&#32654;&#23481;&#38498;](http://www.snownes.com/xwzx.asp) [&#32654;&#23481;&#21152;&#30431;](http://www.snownes.com/xwzx.asp)

---

