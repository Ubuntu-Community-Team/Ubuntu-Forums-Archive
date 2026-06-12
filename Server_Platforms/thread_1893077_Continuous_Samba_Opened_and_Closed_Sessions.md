---
title: "Continuous Samba Opened and Closed Sessions"
date: 2011-12-09
forum: Server Platforms
---

### Post by dudemanbubba on 2011-12-09
Having troubles with my Ubuntu network.  Things had worked fine for about a year.  We added a couple new people / workstations and things worked as well for a short period of time.  Now we are experiencing frequent network dropouts to the server.  The auth.log file contains consistent and frequent closed then reopened sessions.  The following is a snippet from the log file:

```
Dec  9 09:17:17 dcls1 smbd[27083]: pam_unix(samba:session): session opened for user kprzeclawski by (uid=0)
Dec  9 09:17:31 dcls1 smbd[27084]: pam_unix(samba:session): session opened for user ecanlas by (uid=0)
Dec  9 09:18:38 dcls1 smbd[27086]: pam_unix(samba:session): session opened for user ecanlas by (uid=0)
Dec  9 09:21:02 dcls1 smbd[27094]: pam_unix(samba:session): session opened for user ecanlas by (uid=0)
Dec  9 09:23:26 dcls1 smbd[27128]: pam_unix(samba:session): session opened for user ecanlas by (uid=0)
Dec  9 09:27:23 dcls1 smbd[27171]: pam_unix(samba:session): session opened for user kprzeclawski by (uid=0)
Dec  9 09:27:30 dcls1 smbd[25941]: pam_unix(samba:session): session closed for user ecanlas
Dec  9 09:32:23 dcls1 smbd[27208]: pam_unix(samba:session): session opened for user kprzeclawski by (uid=0)
Dec  9 09:33:35 dcls1 smbd[26523]: pam_unix(samba:session): session closed for user kprzeclawski
Dec  9 09:33:53 dcls1 smbd[27007]: pam_unix(samba:session): session closed for user ecanlas
Dec  9 09:37:23 dcls1 smbd[27255]: pam_unix(samba:session): session opened for user kprzeclawski by (uid=0)
Dec  9 09:38:06 dcls1 smbd[27084]: pam_unix(samba:session): session closed for user ecanlas
```

We exhausted all efforts to determine if this was hardware related on the network side.  It started with one workstation with the others not effected.  Then it started to happen to all of them after a few days.  Other than the opening and closing, I don't see anything in the logs that would tell me why they are opening and closing.

I am remote to this site and need to do all of my troubleshooting through vpn connections so any help is appreciated if you have experienced anything like this.

---

### Post by dudemanbubba on 2011-12-09
Running Ubuntu 10.04 server... Samba 3.4.7.

---

### Post by redmk2 on 2011-12-09
Did you add the users to the Samba users database?```
sudo smbpasswd -a
```

---

### Post by dudemanbubba on 2011-12-09
Yes.  That was done.  Are there logs that should provide details of why the connections are closed and opened like they are?  The NIC is showing no lost packets or anything.

I have tried to eliminate the PAM from the equation by changing the security = share in lieu of user in the smb.conf.  It seems to have been stable since I did that for about the last half hour or so.

---

### Post by dudemanbubba on 2011-12-20
For anyone interested, this ended up having nothing to do with the server.  We had Canon come in and install our new printer and they inadvertently assigned the printer the same ip address as our server.  Ugh!  The two had been fighting for dominance ever since.

Is there a test or utility that would have shown me that this was the issue?  I physically went to the remote site and it was only the fact that I needed to print something that I stumbled across the problem.  Had I not needed to get the printer's ip, I would probably still be screwing around with it.

---

### Post by redmk2 on 2011-12-20
> **dudemanbubba said:**
> For anyone interested, this ended up having nothing to do with the server.  We had Canon come in and install our new printer and they inadvertently assigned the printer the same ip address as our server.  Ugh!  The two had been fighting for dominance ever since.

Is there a test or utility that would have shown me that this was the issue?  I physically went to the remote site and it was only the fact that I needed to print something that I stumbled across the problem.  Had I not needed to get the printer's ip, I would probably still be screwing around with it.

Only my System Administrators provision anything in my networks.  In addition we keep an assets manifest.  This includes the IP address, MAC address, manufacturer, primary user, etc.

Never let a vendor muck about in your network.

---

### Post by dudemanbubba on 2011-12-20
Unfortunately, our main office is in Florida and this site is in DC.  I have no IT staff there.  I knew the printer had been delivered and was being used for copies and fax only.  Someone up there asked the Canon guy to connect it and I had no idea...

Regardless, is there a network utility that could tell you that you had two identical ip's on the network?

---

### Post by redmk2 on 2011-12-20
> **dudemanbubba said:**
> Unfortunately, our main office is in Florida and this site is in DC.  I have no IT staff there.  I knew the printer had been delivered and was being used for copies and fax only.  Someone up there asked the Canon guy to connect it and I had no idea...

Regardless, is there a network utility that could tell you that you had two identical ip's on the network?

I hate bureaucracies.  I'm paranoid enough to query anybody messing with equipment on my network.  Whether you asked for it or someone else did, you should know what the vendor did in your little patch of the world.

There are applications that will query the network for provisioning information.  But since you can't have the same IP on two **active **interfaces it really won't show up.  You need to know it to see it.  Kinda like you did.

Your experience is something you will carry forward so it won't happen again.

[**_[COLOR="Blue"]Here is some info[/COLOR]_**]("https://www.google.com/search?q=network+provisioning+linux+&btnG=Go!#pq=network+provisioning+linux+&hl=en&cp=16&gs_id=1j&xhr=t&q=network+inventory+linux&tok=uZ8SsjZgSX5RPWfUMQPgkg&pf=p&sclient=psy-ab&source=hp&pbx=1&oq=network+inventor+linux&aq=0&aqi=g1g-b1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=da59a917d7d0a4a2&biw=1099&bih=628") on network inventory software

---

