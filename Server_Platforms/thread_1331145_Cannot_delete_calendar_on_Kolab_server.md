---
title: "Cannot delete calendar on Kolab server"
date: 2009-11-19
forum: Server Platforms
---

### Post by t.rei on 2009-11-19
Hi,

I am currently running out of idea's or to be more precise I don't have any.

I am running a kolab2 server on an ubuntu karmic server.
And I created a calender "Work" using Kontakt on a Kubuntu Karmic machine.
The calender was created, I was able to add entries. 

Now I wanted to delete the calender, but I always get this:
I do:
-> right-click "My Work" -> remove
-> Are you shure? Remove.
-> Cannot delete your standart resource.

The same thing happens if I use the little delete icon.

Now I figure, since the client is almost a fresh install, there might be something wrong with permissions maybe on the server? 

I would be most gratefull for any insights.

Thanks.

---

### Post by t.rei on 2009-11-19
Oh, can this please be moved to desktop-environment. It seems to be a problem in Kontact.

I used evolution and added a simple imap connection to my account on the kolab server.
I was able to delete any folder in the list (they showed up as regular imap-folders) and thus was able to delete the kalenders that were wrong.

So there seems to be a twist in the create/delete kalender / imap / kontact communikation. 

I'll now go see if there is any current bugreport on this somewhere. If you can point me to it, it would be sweet. 

This means that the contents of this thread is not soved, but there is a workaround: using plain imap connection to delete not-wanted folders.

---

### Post by tmcastberg on 2009-11-19
> **t.rei said:**
> 
I am running a kolab2 server on an ubuntu karmic server.


Did you use the repository packages for setting it up? If so, did you have any issues with it? I can't for the life of me get it going...


Cheers,
Tor Magnus

---

### Post by t.rei on 2009-11-19
Yes, the one from the repos. It's been a while, but I cannot recall any unusual problems setting it up. Using it however was never as smooth as hoped for. ;)

What was the 'official' background for evolution in the opensourceworld again?

---

### Post by tmcastberg on 2009-11-19
Hm, well it's either Kolab or Zimbra I think and I'm finding zimbra a bit OTT I think...

I seem to have it partly running now (my own fault), but I'm getting "Could not bind to LDAP server: Invalid Credentials" in the Kolab-webadmin interface. Ring any bells?

Cheers,
Tor Magnus

---

### Post by tmcastberg on 2009-11-19
Ok, it seems I found the problem.

/etc/kolab/session_vars.php was not configured at all, but as kolab.conf contained all the needed values it was pretty straight forward to configure it. :)

---

