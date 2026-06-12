---
title: "Changes to Samba, does this require rejoining workstations to domain?"
date: 2008-08-21
forum: Server Platforms
---

### Post by trentmc on 2008-08-21
Hi

I have a new ubuntu server 8.04 box running as a PDC.  I have had a few dramas with an accounting package sitting on one of the shares.  Due to these problems i have been playing around with the smb.conf file (...oplocks etc).  

After changes I have run 'testparm' and restarted samba.  Should these changes now apply to current smb users? I have tried rebooting the server.

I have manually logged users off from their workstations and back on, and I don't think that is enough.

Do i need to rejoin all machines to the domain again manually? And if so, is there a way to avoid having to re-setup each user on their particular workstation?  (ie.. copy my docs, faves, desktop & import outlook PSTs from the old profile to the new one) 

All workstations are Win Xp.

Any advice?  Or am i going to have to suck it up and feel the pain?

Trent

---

### Post by trentmc on 2008-08-22
anyone? anything?

- Trent

---

### Post by bab1 on 2008-08-22
> I have manually logged users off from their workstations and back on, and I don't think that is enough.
 What causes you to think this?  Is something not working?

---

### Post by trentmc on 2008-08-22
When i pull the smb status i can see the share that i change disabled oplocks is not disabled for these users.

I also made a cosmetic change, by changing the display name, but this doesn't change for existing users.  

- Trent

---

### Post by bab1 on 2008-08-22
I'll bet that's an oplocks problem.  I believe the smbd daemon forks and rereads the smb.conf file each time it gets a request and the dies when done.  You can remap the users shares for the second issue.  What is the oplocks problem?  Are you crossing physical drives?

---

### Post by trentmc on 2008-08-23
thanks ... will remap for the other issue (not a biggie anyway)

Basically we have an accounting package that sits on a shared drive.  If this is accessed by one user there is no problem.  But as soon as a 2nd, 3rd ...etc user attempts to use this package its welcome to slowville.  Unfortunately the support guys for the accounting package have given me the classic fob "LINUX, SAMBA UNSUPPORTED...go to hell" so i have no recommendations or sample configs from that side.

Does ubuntu support kernel level oplocks?  ( i noticed this in some smb confs i have googled)  

Should i be disabling oplocks just for that share or globally?

What about fake oplocks?

Anyone have a sample config for a similar setup?

Also am not crossing physical drives.

Trent

---

### Post by bab1 on 2008-08-23
I'm no expert on oplocks.  I've never had users run an app from a Samba share.  ;-) Ideas ???  Store data yes.  Run the app no!

I've read a little and it seems that your problem might indeed be an app problem, but you will never win that one.  Oplocks is a Windows thing that Samba institutes.  It appears that the later (2.4 on) kernels are oplocks aware.

There is some good information [[COLOR="DarkOrange"]**here**[/COLOR]]("http://www.superbase.com/services_tech_support_oplocks.htm") , [[COLOR="Green"]**here**[/COLOR]]("http://oreilly.com/catalog/samba/chapter/book/ch05_05.html"), [[COLOR="Blue"]**here**[/COLOR]]("samba_reference_guide/24_locking_08.html"), and of course [[COLOR="Magenta"]**here**[/COLOR]]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html").

---

### Post by trentmc on 2008-08-23
thanks mate

will give it another bash this week!

---

### Post by bab1 on 2008-08-23
Trent,

I have an idea.  If you can separate the data from the app, I would do so.  Then I would make the app "share" read only and drop the oplocks.  I'll bet there are executables being locked needlessly.

---

### Post by trentmc on 2008-08-24
Yeah its definitely locking thats the prob.  Unfortunately I think separating the data and the app will be way too much hassle than its worth (.....well at the moment, when i still have hope of resolving it ;) )

I have little to no experience with this software package, and am not envisioning too much assistance from their support.

This was all working nicly on a previous RH box, all on the one share.  This is basically a straight copy of data from that share to the share on the new server.

Just in the process of setting up some Vm's to do some more testing now.

wish me luck!

Trent

---

### Post by bab1 on 2008-08-24
Must be Monday where you are!  I'm surprised that the RH share worked.  was it an earlier kernel?  Good luck with what ever you do.  Maybe the boss will find another accounting package.  I remember having to support a DOS app on W2k for awile.  it was no fun.

---

### Post by trentmc on 2008-08-24
It is monday indeed here in sunny Melbourne Australia!

yeah old kernel and old ver of samba too.  Don't think i will be getting the boss to change the accounting package, our org is tight on the old $$$$ (not for profit org)

Trent

---

