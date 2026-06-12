---
title: "How do I disable the password prompt at the login screen AFTER LOGOUT"
date: 2011-11-19
forum: Security
---

### Post by amadis2009 on 2011-11-19
When I startup my computer it automatically logs in without asking for a password. I want it to do the same when I logout and log back in, but it keeps asking for the password. Would prefer automatic login both ways. 

Ubuntu 11.04

---

### Post by Bachstelze on 2011-11-21
Er, just don't log out? What's the point of logging out in the first place if anyone can log back it ?

---

### Post by amadis2009 on 2011-11-21
Wow! What a supremely unhelpful post. Why even bother wasting the energy typing?

To answer your question. I sometimes log out and log back in to update some sort of change I've made on my computer and it is tiresome tying the password in repeatedly.

Thanks for your assistance.

---

### Post by gsgleason on 2011-11-22
What a sarcastic response.

Have you looked at this: [http://ubuntuforums.org/showthread.php?t=123116](http://ubuntuforums.org/showthread.php?t=123116)

---

### Post by amadis2009 on 2011-11-22
If my response was sarcastic, it was only because Bachstelze's response was so rude. And pointless as well. Answering the question "How can I do X?" with "Just don't do X And why would anyone want to do X anyway?" is in my mind, extremely rude.

Thank you though, for your helpful reply. I have to admit the solution described in the thread you linked to is a bit complicated for me. I'll try to have a go at it when I have some more time, but I wonder if there is a simpler solution. I've been on Ubuntu since Lucid and never had to enter a password at login before until last week when I did a clean install.(I upgraded to Oneiric and then remembered how much I prefer Gnome to Unity.) So I wonder what has changed.

---

### Post by I_can_see_the_light on 2011-11-23
Would it not be possible to set a timer before a user is logged in? I'm not using Ubuntu right now but it used to be possible to do this from the GDM setup screen.

---

### Post by amadis2009 on 2011-11-23
I'm not sure I understand. What would the timer do?

---

### Post by I_can_see_the_light on 2011-11-23
> **amadis2009 said:**
> I'm not sure I understand. What would the timer do?

It would log you in automatically after a specified time unless you touch the keyboard. There used to be a setting for that somewhere in the 'login screen settings' or whatever it's called.

I might be mistaken but i think it used to work the same way regardless of wheather you just booted your machine or logged out.

---

### Post by cariboo on 2011-11-23
> **I_can_see_the_light said:**
> It would log you in automatically after a specified time unless you touch the keyboard. There used to be a setting for that somewhere in the 'login screen settings' or whatever it's called.

I might be mistaken but i think it used to work the same way regardless of wheather you just booted your machine or logged out.

The options you're talking about haven't been available, since 10.04, when Plymouth and grub2 were added, the ability to customize GDM was no longer available.

I'd suggest the op try the solution that he has already been given in vbox, before trying to implement it on a live install. There isn't a gui, or quick solution available.

If you want to do something complicated, sometimes there is only a complicated solution.

My suggestion would be to let muscle memory type your password.

---

