---
title: "Pardon the Newbie"
date: 2005-02-17
forum: Server Platforms
---

### Post by camrocks on 2005-02-17
Hey guys/gals

a redhat server convert here, love the product, but a couple of issues, a simple pointer will do.

1) When you do your smb.conf, and go to recompile it with make, it dows not make any changes, but there is no modification GUI for samba as standard. how do I get it up as a PDC for a primaraly windows network without doing this, and how do I add samba users, is it just via the smbusers -a command??



2) where do I make changes to firewall ports?? Currently I have installed it and had a bit of a play, but I need to open some ports. how pls???

love the distro, seems simple, i'm prob just missing something or haven't configured something. Going to be using this as the PDC and AUTH server, so I want to get it right, and want to run my business on it, so happy to mirror you guys, or host an IRC server for you once I have it up and running.

regards,

---

### Post by Rottweiler on 2005-02-17
[QUOTE=camrocks]1) When you do your smb.conf, and go to recompile it with make, it dows not make any changes, but there is no modification GUI for samba as standard.[/quote]Call me clueless but I've never heard of someone trying to compile smb.conf with make. You just make changes to /etc/samba/smb.conf and if samba is running it will pick up the changes almost immediately.
   
 I've never seen a samba configuration gui tool that was anything other than deficient. Better to learn to edit the config file by hand, especially if you're going into the complexities of the domain security model and such. I'd start by reading the docs at [http://www.samba.org]("http://www.samba.org") and then maybe pick up a copy of 'Using Samba' from O'Reilly.
   
 > 2) where do I make changes to firewall ports?? Currently I have installed it and had a bit of a play, but I need to open some ports. how pls???For simple firewall setups install firestarter. It's a gui config tool that's quite good. Go to [http://ubuntuguide.org/#firestarter]("http://ubuntuguide.org/#firestarter").

---

### Post by camrocks on 2005-02-17
SORRY!, usually you'll go /etc/init.d/smb restart in redhat, not make.... thanks for your hints, i'll givem a go....

:-) :-)

---

### Post by rufius on 2005-02-17
[QUOTE=camrocks]SORRY!, usually you'll go /etc/init.d/smb restart in redhat, not make.... thanks for your hints, i'll givem a go....

:-) :-)[/QUOTE]
 /etc/init.d/ exists in Debian/Ubuntu and the samba/smb executable script should be there.

---

### Post by camrocks on 2005-02-17
Yeah, tried that, but the script does not seem to be there. anyways, it can see the samba domain now, but I can't logon to it....   any ideas?

---

### Post by Rottweiler on 2005-02-17
[QUOTE=camrocks]Yeah, tried that, but the script does not seem to be there.[/QUOTE]If you've installed samba but these aren't there I'd be worried:```
$ ls -l /etc/init.d/samba
 -rwxr-xr-x 1 root	 root		 1856 2004-12-17 08:39 /etc/init.d/samba
 $ ls -l /etc/rc2.d/*samba
 lrwxrwxrwx 1 root	 root		 15 2004-12-17 21:40 /etc/rc2.d/S20samba -> ../init.d/samba
 
``` I'd probably attempt a re-install.

---

### Post by rufius on 2005-02-18
I suspect he doesn't have samba-server installed maybe?

---

### Post by camrocks on 2005-02-18
ok.......

For those others that are redhat converts, this is how you do it

instead of /etc/init.d/smb restart

you have to stop the server then start it like this

/etc/init.d/samba stop

/etc/init.d/samba start

the restart command does not seem to work....

However, I now have the problem of:

When logging onto the domain I get ...

"the following error occurred attempting to join domain "FIFTHSTREET"

The network path was not found


I have enabled domain logons

I have enabled domain and prefferd master

OS level is 65

I have set the password

I get the logon window when trying to join the domain, it just cannot seem to negotiate the transaction. 

any ideas??

---

### Post by camrocks on 2005-02-18
well, sorry bout that, I just figured out that on in "hosts allow" :-)

ummmm, now I have bad username/password and I have set the passwords for users using smbpasswd -a user command already

ideas?

---

### Post by camrocks on 2005-02-18
sorry, and in addition to this, I can access the server via "my network places" in winblows, and my password and username work there, just won't work for domain logons whyfor??

---

