---
title: "Parental Controls WHITELIST not working"
date: 2007-01-22
forum: Ubuntu Christian Edition
---

### Post by pmdubuc on 2007-01-22
I have Ubuntu CE 6.06 installed and I'm trying to configure the parental controls with the GUI (System->Administration->Configure Parental Controls).  When I click the "Users Not Filtered" button and add a user login id, it seems to have no effect.  That user's web access is still restricted.  The comment in the configuration file says:

#users names, who, if basic
#proxy authentication is 
#enabled, will automatically
#not be filtered.

So what is "basic proxy authentication and how to I enable it, or find out if it is enabled by default.  I understand that Ubuntu CE uses dansguardian with tinyproxy.  I've searched the internet trying to find information on how to fix this problem and haven't found anything useful.

Any help would be appreciated.   Thanks,

Paul Dubuc
](*,)

---

### Post by mhancoc7 on 2007-01-22
> **pmdubuc said:**
> I have Ubuntu CE 6.06 installed and I'm trying to configure the parental controls with the GUI (System->Administration->Configure Parental Controls).  When I click the "Users Not Filtered" button and add a user login id, it seems to have no effect.  That user's web access is still restricted.  The comment in the configuration file says:

#users names, who, if basic
#proxy authentication is 
#enabled, will automatically
#not be filtered.

So what is "basic proxy authentication and how to I enable it, or find out if it is enabled by default.  I understand that Ubuntu CE uses dansguardian with tinyproxy.  I've searched the internet trying to find information on how to fix this problem and haven't found anything useful.

Any help would be appreciated.   Thanks,

Paul Dubuc
](*,)

I have not figured out how to set it up either. I left the option in the GUI for those who may know how to get it setup. Hopefully someone can shed some light on the situation.

God Bless, Jereme

---

### Post by tonhou on 2007-01-23
Unfortunately this is an issue that requires further tuning for it to work. It requires user authentication for the proxy server (tinyproxy). I am not sure if/how tinyproxy allows this. So there is a question mark over whether this can be done with this DG/Firehol/Tinyproxy arrangement.

I shall do some investigating on it in the next week or so and see if there is a way ahead.

--Tony

---

### Post by tonhou on 2007-01-30
OK, after some research the short answer is that this is not possible with the current tinyproxy package.

About a year ago an attempt was made to add this feature via a patch as discussed here:
[http://sourceforge.net/mailarchive/forum.php?thread_id=9466954&forum_id=2653](http://sourceforge.net/mailarchive/forum.php?thread_id=9466954&forum_id=2653)

The poster actually built an rpm of the patched version, but unfortunately the link is now dead.

So, unless such a patched edition of tinyproxy comes to light user authentication isn't possible.

--Tony

---

### Post by mhancoc7 on 2007-01-30
Thanks! I will probably remove the option from the GUI then. 

Jereme

---

### Post by pmdubuc on 2007-02-01
Thanks for looking into this, Tony.

---

### Post by Aurora Borealis on 2007-02-21
> **mhancoc7 said:**
> Thanks! I will probably remove the option from the GUI then. 

Jereme

How can we do this? And is there a way just to disable this feature? I tried to enter my yahoo address book, and got this:

S T O P
Access to the page has been denied.

URL: http:/
ICRA chat PICS labeling level exceeded on the above site.

Please contact the Network Administrator if you think there has been an error. 

And an online dictionary...no luch there either...Is there a way to disable this feature?

---

### Post by mhancoc7 on 2007-02-21
> **Aurora Borealis said:**
> How can we do this? And is there a way just to disable this feature? I tried to enter my yahoo address book, and got this:

S T O P
Access to the page has been denied.

URL: http:/
ICRA chat PICS labeling level exceeded on the above site.

Please contact the Network Administrator if you think there has been an error. 

And an online dictionary...no luch there either...Is there a way to disable this feature?

Yes, you can do one of two things.

1. Install the latest beta version of the GUI located here.
[http://www.ubuntuforums.org/showthread.php?t=355935](http://www.ubuntuforums.org/showthread.php?t=355935)

This version has many improvements. One of which allows you to easily adjust the PICS (image) filtering. 

2. Run this command in terminal.

```
sudo gedit /etc/dansguardian/pics
```

Then simply edit the file to turn off the PICS (image) filtering.

Hope that helps, Jereme

---

