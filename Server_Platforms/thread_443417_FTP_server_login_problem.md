---
title: "FTP server login problem"
date: 2007-05-14
forum: Server Platforms
---

### Post by freebeer on 2007-05-14
Hi folks!

I've set up an FTP server on my Dapper box.  I am able, from within the LAN to login and transfer files.  That seems to be pretty smooth.  However, when I try to login from outside the LAN (I have a dynamic DN) I can't seem to log in.  I can connect... I see the login response and the login message but I get an error to the LIST command that says:


"Transfer channel can't be opened. Reason: No connection could be made because the target machine actively refused it."

Am I right in interpreting that the server some how isn't authenticating the user?  Any ideas what I might be doing wrong?

It's not an anonymous login, FWIW.

Thanks!

---

### Post by craigp84 on 2007-05-14
Hi FreeBeer,

Sounds like port 20 is unreachable from outside.

Is there a firewall in between, and only port 21 has been allowed to pass through?

Allow port 20 through, and all should be rosy!

Hope this helps,

Craig

---

### Post by freebeer on 2007-05-14
Thanks for your reply!

hmmm... I've got the server configured to listen on Port 1980, and I've forwarded that port on the router to the server. (and I'm logging in using that port, of course.)  I did not, however, configure the router to forward port 20.  Never thought of that.  But that's only for the server, isn't it?  The router shouldn't be blocking outgoing ports, should it?  *scratches head*

I'll dig into some more once I get home.  Thanks for the tip!

---

### Post by craigp84 on 2007-05-14
Hi,

With the error your getting i was thinking it was setup for active rather than passive ftp - in which case it will need that second port.

If it's setup for passive, and you see PASV in your client, just do a tcpdump (or use wireshark) to see exactly what's going wrong.

-c

---

### Post by freebeer on 2007-05-14
Hi again!

Thanks for the tip (again).  :)  It's definitely accepting passive mode from within the LAN (but, of course, I have no problem connecting/transferring from within the LAN).  Now that I'm at home, I can't check that setting from the office until tomorrow.  I'm pretty sure that it's going into passive mode, but I'd have to check to be sure as I wasn't paying attention to that particular mode.

---

### Post by freebeer on 2007-05-15
Update:

The client does go into passive mode.  Then issues the LIST command but it's getting an error:

```

Transfer channel can't be opened. Reason: No connection could be made because the target machine actively refused it.

```
(Filezilla client error)

```

No connection could be made because the target machine actively refused it

```
(SmartFTP client error)

I forwarded the ports, as you suggested, but I later realized that when in passive mode, it uses a range of ports, which are not yet forwarded in the router.  I'll play around with that once I get home.  (This bouncing between locations is getting annoying :D)

If I login using active mode only, I get a time-out error after the LIST command is issued.  (no listing is shown, of course.)

The errors that I'm getting "actively refused" implies to this newbie that the server is rejecting the request as opposed to a time-out error due to lack of communication through ports.  (The error comes back almost immediately after the LIST command is issued.)  So continuing on that line of reasoning, would there be a permissions problem that I'm somehow missing?  I've checked the .conf file and all seems well there... the users I'm loggin in with appear to have the rights to issue the LIST command.  I've even changed the folder's ownership to the ftpgroup just in case that was being an issue but that doesn't appear to have helped.

Of course, that line of reasoning above doesn't explain why I can do it within the LAN but not through an internet connection.  Another observation:  SmartFTP, when it connects, reports the IP addy of the Domain Name (79.x.x.x).  Filezilla, once it enters passive mode, reports the addy of the server as the internal (LAN) addy:

```

:	227 Entering Passive Mode (192,168,1,103,251,119).

```

Question... are the two last digits possibly the ports it's trying to use?

Thanks for any insight that you can offer!

---

### Post by freebeer on 2007-05-17
*bump*

---

### Post by craigp84 on 2007-05-17
Sorry Freebeer, i missed your reply before.

The fastest way to resolve this will be to capture exactly what each box sees during an ftp connection attempt.

I think you mentioned you were running on non-standard ports before, so don't limit your captures in any way shape or form - capture everything.

Use either tcpdump (recommended because it just works) or wireshark to do the recording.

I hope this provides the necessary enlightenment, but if not, post back your findings of the packet capture. Specifically what packets (and on what ports) are packets reaching the server?

-c

---

### Post by freebeer on 2007-05-17
Thanks for the reply!

I'll do as you suggest.  I'm unfamiliar with tcpdump, but I'll give it a go if it gets to that.  I'll try to tap into a friend of mine who has more experience with FTP servers than I - and we'll be able to do it from both ends (me here on the server-side and him on the internet-side.)

---

### Post by morningboat on 2007-05-18
Your problem here is that you uses a router in between the client and server, while your client tried to link directly to your server rather than the router so that the data connection failed. Two ways to solve your problem:
choice i, select your ftp client's option and choose to substitute the PASV IP with the incoming server's IP. (Take the [CrossFTP ]("http://www.crossftp.com")as an example, check the option at: Site Manager -> Options -> Substitute PASV IP with Server IP.
choice ii, chose PORT (active mode) on your FTP client to transfer the files. (choose Site Manager -> Options -> Connection Mode -> PORT).

---

### Post by freebeer on 2007-05-18
Thanks for your help, folks!

I was able to get it working, finally, by using active mode, but only after changing the port to a standard one (and of course forwarding the ports in the router).

This will do me for now -- the server is intended for very infrequent access with relatively low transfer volumes.

Much appreciate your efforts!

---

### Post by burnercan on 2007-06-07
I'm having pretty much the same problem... on a D-Link 524 router. In pasv mode, it gets as far as "Entering pasv mode xxx.xx.xx.xx.xxx.xx" and in port mode i get "425 Can't open data connection" Seems like port 20 is not accessible. So where do I need to open port 20? If I set either the public or private ports to 20, I can't connect at all... Any ideas? This is my first crack at an FTP server, does it show???

---

### Post by freebeer on 2007-06-08
Are you trying to log in from an internal (LAN) or an external (internet) connection.  If it's an external connection, you'll have to forward the port you're using (20?) to the IP of the computer running the server.  In passive mode, I believe the ftp server and the client negotiate a separate set of ports.  You'd have to open a range of those ports in the router to make it work.  At least in theory.  Although I did that with my D-link router, I could never get passive mode to work - maybe the router isn't up to the task?  I dunno.  But by forcing active mode only, I was able to get it to work.

HTH

---

### Post by burnercan on 2007-06-08
These are the configs I've tried...

[IMG]http://www.chezricci.com/Images/Picture 1.png[/IMG]

The Private IP is static. Set like this, the client can log in, and gets as far as "Entering passive mode" (if in pasv) or "425 can not open data connection" in port

If I change the Private port to 20, the client says the server is unreachable. Is that where I should be opening port 20?

Thanks!!!

---

### Post by freebeer on 2007-06-08
Yours is a little different than mine (different router model, I mean).  I'm not really even sure what the Virtual Server's purpose is.  I just went to the IP forwarding section and forwarded the ports there.  You might want to try just that - after disabling the Virtual Server (it might be getting in the way).  I have to head out, so I don't have time right now to take a screenie to demonstrate what I mean.

---

### Post by burnercan on 2007-06-08
I wondered that at the begining... but as I was unable to find a "Port Forwarding" page, I kinda assumed that this Virtual Server thing was just that under a flashy name... I'll keep on trying!

---

### Post by freebeer on 2007-06-08
It seems they are using different terminology (damned marketing guys!).  It appears that the Virtual Server is the right place to go for single port forwarding.  A range of ports is done under the "firewall" setting, from what I can gather from their website.  I set up a firewall rule in mine using the range 20-21 and I got it to work (in active mode only).  The client will have to set his configuration up for active mode, too.  I believe the default is that most ftp clients will log in in active mode, then automatically switch to passive mode.  It's the passive mode that messed me up.  Although I forwarded the range of ports that my ftp server was going to use in passive mode, I couldn't get it to work.  So I just switched back to active only, which did work, and is fine for my purposes.

---

