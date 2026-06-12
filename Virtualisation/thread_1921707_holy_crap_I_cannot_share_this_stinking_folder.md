---
title: "holy crap I cannot share this stinking folder"
date: 2012-02-07
forum: Virtualisation
---

### Post by Ms. Daisy on 2012-02-07
I've got virtualbox installed on my Ubuntu 11.10 host.  I've got ubuntu 10.04 as a guest.  All is well.

Now I want to share a folder from the host to the guest.  BLARGH! There is nothing that I cannot overly-complicate.

I'm in the user group.  I can see the shared folder, but I get this:
```
You do not have the permissions necessary to view the contents of "sf_folder".
```
Grr... 

will this work?
```

sudo pretty please share sf_folder
```

---

### Post by Morbius1 on 2012-02-07
If you look at the ownership and permissions of the /media/sf_ folders on the guest:
```
ls -al /media
```You will notice that it's accessible to root and members of the vboxusers group.

It's possible that you are not a member of that group so add yourself:
```
sudo gpasswd -a msdaisy vboxusers
```Then logoff and logon ( not reboot ) and see if that fixes it.

---

### Post by Ms. Daisy on 2012-02-07
Thanks. I think this is where I get confused.  I added my host user to the host vboxusers group a while ago and successfully shared folders in a different VM.

So where exactly do I type in 
```
sudo gpasswd -a msdaisy vboxusers
```Does it go into a terminal in the **guest** or the **host**?  The virtualbox manual is a bit vague on this point.

Also, am I adding the **host** username into the user group, or am I adding the **guest** username? Again the manual is vague.

---

### Post by Morbius1 on 2012-02-07
All of this is happening on the guest. So it's the guest user name and the command is run on the guest OS.

---

### Post by Ms. Daisy on 2012-02-07
Aha! Thank you!  It seems I added my host user in the group on the host the first time, so I did it completely wrong. But it didn't matter for the other VM because it was running as root (and shares are accessible to root automatically).

---

