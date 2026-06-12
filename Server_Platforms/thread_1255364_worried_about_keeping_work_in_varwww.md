---
title: "worried about keeping work in /var/www"
date: 2009-09-01
forum: Server Platforms
---

### Post by morganpatrick on 2009-09-01
Hi,

I have a localhost running on my machine, simply for development and testing. I'm not 'serving' to anyone. all my files are in /var/www, and this worries me, because all my other documents are in /home which is on a different partition, in case my root partition gets messed up, but obviously /var/www is in root.

Also, when I delete something from my localhost, it's gone for good. Is there a way I can have localhost alias to /home/username/localhost?

FOLLOW UP QUESTION: If i'm testing something in windows via vmware, can I make that localhost point to /home/username/localhost in linux? This is a less important question because I think I can probably figure it out if you don't know.

Thank you!

---

### Post by hessiess on 2009-09-01
Open /etc/apache2/apache2.conf with your favourite editor and change ServerRoot to a location in your home dir.

---

### Post by terazen on 2009-09-01
If you go into /etc/apache2/sites-available there should be a file in there called default.  You can change your default folder from /var/www/ to whatever you like.  Just make sure whatever new folder you create has the right permissions for apache view.

If you change the default file just restart apache afterwards with `sudo /etc/init.d/apache2 restart`.

---

### Post by morganpatrick on 2009-09-01
I did both of these and it worked! thank you.

How do I mark the thread as "solved"?

---

### Post by cariboo on 2009-09-01
I marked this thread solved for you, next time look under Thread Tools at the top of the page.

---

### Post by morganpatrick on 2009-09-02
solved!

---

### Post by windependence on 2009-09-05
Just a bit of post comment from a Linux/Unix veteran.

This is why you should do more partitioning than the default install. Especially, I keep a separate partition for /var as this is specifically for files that grow (or contract) in size. It's a very good idea to make separate physical partitions for /etc, /home, /usr, and /var IMHO. /var is where logs are kept, and if they fail to rotate, they can quickly fill your entire root partition if you don't give /var it's own physical space.

<sigh> this is a symptom of "dumbing down" Linux distros for Windoze users. It used to be that no one would think of just making one or two partitions for Linux, but that seems to be "too confusing" for some users. It's unfortunate IMHO.

For those interested in doing it right, here is some useful information:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/)

[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

[http://tldp.org/HOWTO/Partition/intro.html](http://tldp.org/HOWTO/Partition/intro.html)


-Tim

---

