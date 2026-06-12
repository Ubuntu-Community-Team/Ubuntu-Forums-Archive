---
title: "How to protect from untrusted files?"
date: 2010-10-08
forum: Security
---

### Post by WeAreLinux on 2010-10-08
Hi. How you doing?

I want to start using videos/music files downloaded from untrusted sources (BT,Sharing Forums, etc.). Haven't made this a habit b4 because of the security risks. I want to take steps to reduce the risk & protect my computer from anything malicious. What are some good choices for this?

The biggest step I took so far is using Ubuntu since it's very virus resistant, but other threats do exist out there (rootkits, malicious scripts, etc.). When downloading files from untrusted sources, who knows what may be hidden inside.

Some options I'm thinking about:

1) Using a VM (with Ubuntu installed inside) & playing the files inside the VM. If anything malicious happen, it would be trapped inside & I could easily revert to a clean snapshot.

2) Using AppArmor to restrict what the files or program used to play the files can/can't do. AA seems very complicated though.

Are the above overkill? Would it be sufficient enough to just open these files on a non-admin user account since no access to root or sudo?

All suggestions/information/advice you can provide would be helpful because I'm still a Ubuntu newbie.

Thank You

---

### Post by rookcifer on 2010-10-08
I wouldn't worry too much about it.  Nothing can execute without you giving it permission.  And if such a file asks for your root (sudo) password, be very wary.  Other than that, you could create a user account specifically for this activity.

---

### Post by OpSecShellshock on 2010-10-08
Yeah, the suspicious stuff is pretty easy to spot with Ubuntu. Essentially, if you get the expected media content to play, then it's good (though if you've got something that can check id3 tags or whatever other meta data might be there it likely wouldn't hurt). If you try to play the files and get any errors or messages about needing to do something else, then it's bad and you can just shift-delete it and move on.

---

### Post by linux-hack on 2010-10-08
In my opinion you could make a vm dedicated to this activity and download everything you want without infecting you main system. And if you don't give execution permissions you don't need to worry about malware code.

---

### Post by cariboo on 2010-10-08
We don't support illegal activities of any sort. This thread is closed.

---

