---
title: "how to auto suspend and wol depending on usage?"
date: 2010-01-18
forum: Server Platforms
---

### Post by markp1989 on 2010-01-18
i have a pc that is set up as a torrent slave / file server and media pc i want to set i up so that is goes in to suspend when there is no need for it to be on.


I wnat it to wake at a set time to run a cron script for me, to check if there are any new torrents out, if there are , download an seed to till rtorrent auto stops the seeding (for me thats set at 1:1), then go back in to standby mode, if there are no active downloads then i want it to go back in to standby straight away.

as its also used as a file server, is there any way to have the shares still visable, with the pc in stand by, then when a user accesses it wake up the server, and if there is no activity after a set time out then go back in to standby. 

i would also like it to wol when i try to ssh in to it

as a htpc is runns moovida, i would also like it to only go in to standby mode if i am not playing a video.

thanks for any pointers.


markp1989


what would you recommend the best way to do this?

---

### Post by markp1989 on 2010-01-18
after suspending, i get some probelms with graphics, i have to restart gdm to get the screen back, and it wont let me go in to standby again.

 i think its because of the nvidia driver?

---

