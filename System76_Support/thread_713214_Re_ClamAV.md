---
title: "Re: ClamAV"
date: 2008-03-02
forum: System76 Support
---

### Post by BrownMan_STL on 2008-03-02
How can i update ClamAV? everytime i do (Help Menu/update ClamAV) a dialogue box message displays "you need to be a root to do updates' or somethin like that.  Please Help.

---

### Post by cwej on 2008-03-02
I run the following command from terminal:

sudo clamtk

this opens the GUI as root (sudo), then I'm able to run Help/Update Signatures

Does this work for you?

---

### Post by fallsoff on 2008-03-02
Hi,
If you are still stuck please try this to get added to sudoers group so that you can easily assume root privileges.This from archive to add yourself to Sudoers group if you are not there. YThis allowed me root privliges when I couldnt accomplish anything in Ubuntu 

 [you MUST use visudo to edit sudoers__do NOT use a text editor}:

"Guess I have to visudo it then? How do I do that?

From a terminal (as root):

visudo

You will want to add the following to the file at the end:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Just make sure your username is part of the admin group, and your set. If needed, you can add your username (comrade, or whatever it is) to the admin group with (again, as root):

useradd -g admin comrade

You should now be able to run 'sudo' when logged in as comrade."

Not to dispute the reply you just got. He posted while I was researching as I couldnt remember the exact cmd syntax.
Best,
fallsoff

---

### Post by thinman1189 on 2008-03-03
If you have freshclam installed then it should do it for you automatically. Just search freshclam in synaptic.

---

