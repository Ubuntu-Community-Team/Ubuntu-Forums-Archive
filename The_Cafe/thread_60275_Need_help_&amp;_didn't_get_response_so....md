---
title: "Need help &amp; didn't get response so..."
date: 2005-08-27
forum: The Cafe
---

### Post by thin_king on 2005-08-27
I'm posting in here where it looks like there are more people. :)  [Yesterday I posted in desktop support](http://ubuntuforums.org/showthread.php?t=60117) on a drive access problem I'm having. Every 5 seconds like clockwork I get loud drive clicks on my Thinkpad T23. Like I said in the original post, I have searched, 

[http://lists.debian.org/debian-kde/2001/11/msg00500.html](http://lists.debian.org/debian-kde/2001/11/msg00500.html)

seems others have had this. I *think* it has to do with mount options "noatime" or "nodiratime" but I'm not sure how to set it up so Ubuntu doesn't write logs/sync every 5 seconds.  

Debian, what I'm using now, apparently does this by default also but it's so silent I wasn't even aware of it until this came up in Ubuntu. In Debian I can only faintly hear it if I put my ear right up to where the drive is, so it doesn't bother me at all. With Ubuntu though, it's a much louder train track sound (clack clack, clack clack) every 5 seconds. Very annoying. Thinkpads are normally quiet machines. 

This may or may not be a useful clue. The system is quiet on the login screen, no clicks. It seems to be a service activated after login or at least deactivated during login. 

*Any* help would be welcome. Even just brainstorming possible solutions to try. Thank you for your time.

---

### Post by npaladin2000 on 2005-08-27
The additional information you provided here helps a bit.  I'm going back to your original post and replying

---

### Post by thin_king on 2005-08-27
Thank you npaladin2000. If it is the atime/noatime attribute this might help.

[http://www.faqs.org/docs/securing/chap6sec73.html](http://www.faqs.org/docs/securing/chap6sec73.html)

---

### Post by skoal on 2005-08-27
brainstorming? I just felt a strike of lightning from ear to ear.  Have you tried installing all the 'laptop' tools available in our repos? I haven't used a lappy in along time, but I've read countless threads like yours in these forums over the last five months - drive noise, constant spinning, etc.

Ooops! Was gonna do some forum searches for ya, but server database having problems right now...

\\//_

---

