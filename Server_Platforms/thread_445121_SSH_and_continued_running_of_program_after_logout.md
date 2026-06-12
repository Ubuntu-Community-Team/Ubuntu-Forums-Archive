---
title: "SSH and continued running of program after logout"
date: 2007-05-15
forum: Server Platforms
---

### Post by userthebuntu on 2007-05-15
Hello ubuntu users,

I have ssh access to my ubuntu box and would like to run a program (e.g. irssi IRC) when logged on via ssh and have the very same program instance continue running after logging out or exiting my local ssh client.
Also I would like to be able to log back in after some time and then kinda go back to the interface before logging out and seeing the very same irssi IRC window again.

Is there a way to go about this problem?


Thanks in advance!

Best Regards

---

### Post by weresheep on 2007-05-15
Hello,

The 'screen' program is what you are looking for ("sudo apt-get install screen" if its not installed by default).

See my post [here](http://ubuntuforums.org/showpost.php?p=1855967&postcount=4) for basic instructions on how to use it.

-weresheep

---

### Post by userthebuntu on 2007-05-16
Awesome! Thank you Mr. Sheep!

---

### Post by weresheep on 2007-05-16
You're welcome.

I've only been using 'screen' for a few months, but I can't imagine remote access to my home machine without it. Fantastic program!

-weresheep

---

