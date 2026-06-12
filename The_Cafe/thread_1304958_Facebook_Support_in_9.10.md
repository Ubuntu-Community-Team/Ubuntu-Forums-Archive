---
title: "Facebook Support in 9.10"
date: 2009-10-29
forum: The Cafe
---

### Post by mikebeecham on 2009-10-29
Since Karmic ships out Empathy as it's main IM client, does anyone know if there's Facebook chat support from it?

I would like to stay as gnome-compliant as I can, but this is kind of a dealbreaker for me, as I keep in contact with a lot of overseas friends, and dont always have the web browser open.

---

### Post by dvlchd3 on 2009-10-29
[http://www.google.com/search?q=facebook+empathy+ubuntu](http://www.google.com/search?q=facebook+empathy+ubuntu)

---

### Post by Johnsie on 2009-10-29
wow, it worked out of the box with Pidgin.

There is a bug posted:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/432213](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/432213)

I'm not really impressed by the GUI of empathy, I hope it's skinnable.

---

### Post by Wiebelhaus on 2009-10-29
> **Johnsie said:**
> wow, it worked out of the box with Pidgin.

For real.

---

### Post by mdshaver on 2009-10-30
Although the link above suggesting a workaround for Facebook support in Empathy used to work, I do not believe it works any longer.

---

### Post by rob.arntfield on 2009-11-11
The only way (for me anyways) to enable facebook chat was to remove 
the *pidgin-facebookchat-1.6.0* and head over to the google website. 

[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Download the .deb and install it. It will warn you that you should use the older version in the repositories, ignore it and install anyways. 

Restart Empathy, problem solved.

One last thing, if this doesn't work, close empathy, and delete haze.manager

*sudo rm /usr/share/telepathy/managers/haze.manager*
then kill mission control 5
*sudo pkill mission-control-5*

Then restart empathy again. You should be okay.

---

### Post by hoppipolla on 2009-11-11
> **rob.arntfield said:**
> The only way (for me anyways) to enable facebook chat was to remove 
the *pidgin-facebookchat-1.6.0* and head over to the google website. 

[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Download the .deb and install it. It will warn you that you should use the older version in the repositories, ignore it and install anyways. 

Restart Empathy, problem solved.

One last thing, if this doesn't work, close empathy, and delete haze.manager

*sudo rm /usr/share/telepathy/managers/haze.manager*
then kill mission control 5
*sudo pkill mission-control-5*

Then restart empathy again. You should be okay.

Done :)

Although to be fair I could only get it to work in Pidgin, not Empathy.

I fired up Empathy once and it didn't appear in the list, so I removed that haze.manager file and killed the mission-control-5 process like you said, and it appeared, but didn't seem to add to my accounts properly or connect. It doesn't bother me too much as I like Pidgin, but it's just a shame.. anyone else have this?

---

### Post by hoppipolla on 2009-11-11
I would also like to say that Pidgin is awesome. I mean AWESOME! Like, it's updated more than Kopete and it's more lightweight than Digsby :)

It's not my top favourite for everything, but it always gets the job done! :)

---

### Post by Odin Overland on 2009-11-12
Is anyone having trouble still logging in to Facebook on Pidgin?  I have been having the same issues on Pidgin portable on the lab computers here running Windows as well (portable is saved in my network space).  It fails to log in, every once in a while it throws me a challenge to authenticate, but still won't work.  Either Facebook has done something to make this not work as well, or I haven't quite gotten the perfect mix yet.  I had the same issue on Adium, but it somehow became resolved (don't ask me how).

Would appreciate the help.

---

### Post by hoppipolla on 2009-11-12
> **Odin Overland said:**
> Is anyone having trouble still logging in to Facebook on Pidgin?  I have been having the same issues on Pidgin portable on the lab computers here running Windows as well (portable is saved in my network space).  It fails to log in, every once in a while it throws me a challenge to authenticate, but still won't work.  Either Facebook has done something to make this not work as well, or I haven't quite gotten the perfect mix yet.  I had the same issue on Adium, but it somehow became resolved (don't ask me how).

Would appreciate the help.

As Rob said, go here and replace the Facebook plugin! - [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/) :)

---

### Post by Odin Overland on 2009-11-12
> **hoppipolla said:**
> As Rob said, go here and replace the Facebook plugin! - [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/) :)

This is what I did originally before I ran the command for the facebook plugin, I don't remember it working well before.  I think I had trouble installing or copying the files to the proper folder.

---

### Post by zekopeko on 2009-11-12
This would be far easier if Facebook exposed it's IM service as a XMPP service. There was some talk about that on the facebook blog but it was a long time ago and no word since.

---

### Post by Odin Overland on 2009-11-12
> **Odin Overland said:**
> This is what I did originally before I ran the command for the facebook plugin, I don't remember it working well before.  I think I had trouble installing or copying the files to the proper folder.

I don't know what I did differently this time, but it worked.  Maybe last time (one of my first times on Ubuntu - so be gentle) I think I used the Archive Manager instead of Package Installer...:redface:

Oh well, just happy it works now!  Trial + Error = Embarrassment + Enlightenment

---

### Post by hoppipolla on 2009-11-12
> **Odin Overland said:**
> I don't know what I did differently this time, but it worked.  Maybe last time (one of my first times on Ubuntu - so be gentle) I think I used the Archive Manager instead of Package Installer...:redface:

Oh well, just happy it works now!  Trial + Error = Embarrassment + Enlightenment

hehe cool man! Yeah you'll need to use the Installer, other than that it's a pretty straightforward procedure! Glad it works :)

---

