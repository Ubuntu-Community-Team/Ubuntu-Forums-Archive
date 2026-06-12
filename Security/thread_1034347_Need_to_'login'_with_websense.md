---
title: "Need to 'login' with websense"
date: 2009-01-08
forum: Security
---

### Post by scharkalvin on 2009-01-08
My company uses the Websense Enterprise content filter on it's firewall/server.  I have no problems using a web browser on my Ubuntu workstation (the browser will pop up a window requesting my windows user name and password, then Websense lets me have access to the internet).  However ftp, wget, and other command line internet access programs do NOT trigger a request for login with Websense.  Therefore the only way to perform a software update is to have a web browser open and keep refreshing it.  Is there some Daemon that can be run which will perform this required login handshake with Websense when required to access an IP address outside of the company network (ie: internet)?  It seems that Windows has no problem performing this action internally as I never see a login request from Firefox or IE on my Windows machine.

I don't want to bypass Websense filtering, I want my Linux machine to work with it the same way the Windows machine does!

---

### Post by cdenley on 2009-01-08
> **scharkalvin said:**
> 
I don't want to bypass Websense filtering, I want my Linux machine to work with it the same way the Windows machine does!

Then we would have to know how Windows works with it, unless somebody happens to be familiar with "Websense". In order to use ftp or wget, you have to "keep refreshing" your browser? Does your session with Websense expire or something?

---

### Post by scharkalvin on 2009-01-09
> **cdenley said:**
> Then we would have to know how Windows works with it, unless somebody happens to be familiar with "Websense". In order to use ftp or wget, you have to "keep refreshing" your browser? Does your session with Websense expire or something?

Here is my understanding of the problem:
When you first try to access an outside network address (internet) websense must be requesting a login name and address.  Firefox catches this request an pops up a box where you can enter your windows user name and password, then websense allows access for the entire computer (not just firefox).  It would seem that the login times out after a while but firefox remembers the entered login name and password so it doesn't pop up the box again (unless you exit firefox and start it again).  In windows, the os itself must be performing this transaction.  The reason that I have to keep refreshing the browser would be that unless I request access to an outside URL the transaction with websense to refresh the login won't occur, it is triggered by the program asking for the outside URL.  Programs such as wget can't handle this transaction.  Windows must have a daemon at a lower level doing the dirty work.

Websense is NOT a true proxy, so using the proxy login and password settings doesn't work in this case.  I haven't been able to catch the transaction with wireshark, but that is probably a matter of knowing how to set up the correct filter (or just capture EVERYTHING and sift though tons of packets).

---

### Post by brimlar on 2009-06-05
The way Websense usually works with Windows desktops is that the local user variable (%username%, etc) are passed automatically to Websense -- it's an integrated feature of Websense with Windows desktops.

Linux desktops obviously do not have this local variable, and this is why Firefox gets presented with a Websense prompt -- up until that point, Websense has no idea who you are.

I have also seen the problem where other programs, like FTP clients and such, are unable to "get out" unless you have opened Firefox and passed your credentials.  This is because often all internet traffic is routed through the Websense server, and certain protocols may or may not be filtered based upon the access given to your userid.

There are several things that can be done:

1)  You can ask your Firewall guy if he can exclude a site's traffic from being routed to the Websense server.  They typically don't like to do this, unless it's for very legit things.
2)  Ask your Websense administrator if he can modify the length of time Websense holds your credentials...if he can lengthen it, you won't have this problem crop up so much.

There isn't a way, as far as I know, to get around the necessity for dealing with opening Firefox and entering your credentials in order to secure passage for other applications.  I have not tried joining my desktop to the domain, but I'm sceptical that would work any better because Ubuntu doesn't have the %username% variable, among other things.

---

### Post by The Cog on 2009-06-05
I use this nifty utility for exactly that problem:
[http://sourceforge.net/projects/ntlmaps/](http://sourceforge.net/projects/ntlmaps/)

---

