---
title: "Step by step disk partitioning and lvm"
date: 2011-08-30
forum: Server Platforms
---

### Post by jon_ak on 2011-08-30
[SIZE=2]i hate to start a thread after it has most likely been beat to death at one time or another but... i read most everything i've been able to find in the past week about setting up disk partitioning and using lvm for a server install. i have v11.04 and a 500g drive that i put together as a basis for a test server to see if the powers that be would be satisfied with replacing the current windows 2003 r2 server with this. ok, 'nuff said with the intro...[/SIZE]

[SIZE=2]i follwed some documentation that stated to setup partitioning manually. i failed miserably at this when i thought i had created all the lv for /srv, /home, /srv, /swp etc. when i selected to continue i was given an error stating i hadn't selected a file system. after many attempts i just went back to the beginning and told it to do a guided install with lvm but that is not how i wish to proceed. i understand the os cannot be installed onto a lv so my question is: do you select "install using the entire disk with lvm"? if so, how or where do you find the location where you can set the volume partition sizes and mount them as the designated purpose? as i mentioned, i though i had them all done correctly as each partition was set to mount as /srv for example but i received the error mentioned above.[/SIZE]

[SIZE=2]is there a guide i can pick up somewhere that details this sort of thing? am not a newbie with computers just new to ubuntu/linux and growing weary of all the microsoft nonsense i've had to deal with since nt4 servers.[/SIZE]

[SIZE=2]thanks....[/SIZE]

---

### Post by redmk2 on 2011-08-30
> **jon_ak said:**
> [SIZE=2]i hate to start a thread after it has most likely been beat to death at one time or another but... i read most everything i've been able to find in the past week about setting up disk partitioning and using lvm for a server install. i have v11.04 and a 500g drive that i put together as a basis for a test server to see if the powers that be would be satisfied with replacing the current windows 2003 r2 server with this. ok, 'nuff said with the intro...[/SIZE]

[SIZE=2]i follwed some documentation that stated to setup partitioning manually. i failed miserably at this when i thought i had created all the lv for /srv, /home, /srv, /swp etc. when i selected to continue i was given an error stating i hadn't selected a file system. after many attempts i just went back to the beginning and told it to do a guided install with lvm but that is not how i wish to proceed. i understand the os cannot be installed onto a lv so my question is: do you select "install using the entire disk with lvm"? if so, how or where do you find the location where you can set the volume partition sizes and mount them as the designated purpose? as i mentioned, i though i had them all done correctly as each partition was set to mount as /srv for example but i received the error mentioned above.[/SIZE]

[SIZE=2]is there a guide i can pick up somewhere that details this sort of thing? am not a newbie with computers just new to ubuntu/linux and growing weary of all the microsoft nonsense i've had to deal with since nt4 servers.[/SIZE]

[SIZE=2]thanks....[/SIZE]

Yes there is a guide; complete with pictures.  See [**_[COLOR="Navy"]here[/COLOR]_**]("http://www.linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/"). 

If you have questions post back here for more help.

---

