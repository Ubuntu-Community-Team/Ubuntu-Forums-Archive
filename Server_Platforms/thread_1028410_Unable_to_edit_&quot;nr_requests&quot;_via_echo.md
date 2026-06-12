---
title: "Unable to edit &quot;nr_requests&quot; via echo"
date: 2009-01-02
forum: Server Platforms
---

### Post by caveman8 on 2009-01-02
I'm trying to change the string within 
"/sys/block/sda/queue/nr_requests"
 from 128 to 512 in order to improve performance of a recently installed 3ware hardware RAID controller. 

Whenever I attempt to do so I get an error message.
Below is the command I used and the result:

joe@hilltop:/$ sudo echo 512 > /sys/block/sda/queue/nr_requests
-bash: /sys/block/sda/queue/nr_requests: Permission denied


I am able to edit the file directly if I open it with an editor.  However, those edits do not survive across server reboots.

Since I originally ran in to this I have discovered that Ubuntu doesn't allow echoing values to this file. Instead, one is supposed to edit the sysctl.conf file. This would work, except that I am unable to find the appropriate tokens to add or edit. 

Thus my question boils down to: how can I edit the value of 
/sys/block/sda/queue/nr_requests
so as to have it retain the new value across reboots?

Thanks for any help on this. 

I'm running Ubuntu server 8.04, 64 bit.

Thanks again,

Caveman8

---

### Post by sonidhaval@gmail.com on 2009-12-06
Hey you can add entry in /etc/rc.local for the same. 

Like: 

/bin/echo 512 > /sys/block/sda/queue/nr_requests

Save and exit that file and run this command to check it out.

# source /etc/rc.local

I hope this will work for you..!!

Have a great time..!

---

### Post by ScottNZ on 2010-03-14
@Caveman8:

For what's it's worth, I'm trying to do exactly the same thing for my 3Ware 9650SE Controller, and I'm getting the same "permission denied" error. I'm on Karmic 2.6.31-20-generic; x86_64. Did you have any luck changing nr_requests?

Cheers,
Scott

---

### Post by ScottNZ on 2010-03-14
@caveman8:

Solved it for me. My problem was the way I was executing the command. I was doing this:

[FONT="Courier New"]sudo echo "512" > /sys/block/sdc/queue/nr_request[/FONT]s

D'oh! That will never work. Open a root shell first:

[FONT="Courier New"]sudo sh
echo "512" > /sys/block/sdc/queue/nr_requests[/FONT]

Hope that helps.
Scott

---

