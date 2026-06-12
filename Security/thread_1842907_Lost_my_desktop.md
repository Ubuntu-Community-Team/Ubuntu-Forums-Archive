---
title: "Lost my desktop"
date: 2011-09-12
forum: Security
---

### Post by BushyIII on 2011-09-12
I have a two user system with my account using an encrypted file system and auto login enabled for the other account. I have since eliminated the auto login.

I have not changed my password but after a recent software update my account fails to create a desktop, the other user is unaffected.  

When in terminal I tried ecrypt-mount-private and am presented with a message that the ecrypted directory is not setup correctly.

This is odd as the system has functioned flawlessly for 4 months previous to the update.

Is there anything I can to resolve this?

---

### Post by icarus81 on 2011-09-12
Can you be more specific about the software update? When you say you get no desktop do you mean X dosent start? Try looking at your xorg.conf /etc/x11/xorg.conf maybe a driver update broke support for you video card?

---

### Post by BushyIII on 2011-09-12
Sure, I do not know how to give you the update.

However, here is the experience.  I am using the simple GUI (gnome) on an old Compag PC.  

If I log into the using the GUI I will see my normal background and mouse pointer, after a while I will get this message "unable to update ICEauthority file/home/USER/.ICEauthority", followed by another message "about a problem with the configuration server", and finally there is a message stating: "Nautilus could not create the following required folders:/home/USER/Desktop,/home/USER/.nautilus".

I have found numerous threads of similar messages and have tried the suggestions which ultimately led me to trying the "ecryptfs-mount-private and it's resultant message that it isn't configured correctly.

It seems that others with this problem had change their password using root which created their problem but I did not do that. 

I also typed "ls -al /home/.ecryptfs" and it reported me as the owner.  Although at other times when just logging into the terminal I was greeted with a message that I didn't own the account and that I should follow what was in a README,txt

I am quite new to Linux, I hope this helps.

---

