---
title: "Deleted current kernel by mistake :("
date: 2013-06-09
forum: Server Platforms
---

### Post by doofus2013 on 2013-06-09
Its my first post and afraid its also a cry for help please! Whilst clearing out the old kernels after Ubuntu complained about being low on disk, I didn't really think and went and deleted the current ones too! 

I've worked around the first complaint by finding, downloading and restoring the following using Ubuntu Live USB
[B]vmlinuz-3.5.0-32-generic
[/B]
However next it is complaining about the following, which I can't find to download anywhere...
 [B]initrd.img-3.5.0-32-generic
[/B]
Could I persuade someone to upload this for me please or help on how to quickly save the mess? Don't say restore from backup... Its a home server and I just never got round to getting a full file based backup, and it is (well, was) running my gf's website

I'm hoping this works.....

Thanks in advance for anyone who can save my bacon!

---

### Post by doofus2013 on 2013-06-09
SOLVED!! For the benefit of anyone else who hits this issue... Three hours of Googling and a combination of..

[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

and

[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

and also this random link because it complained it needed the vmlinuz file when running the above steps

[http://download.polytechnic.edu.na/pub/ubuntu/ubuntu/dists/precise-updates/main/uefi/linux-lts-quantal-amd64/current/](http://download.polytechnic.edu.na/pub/ubuntu/ubuntu/dists/precise-updates/main/uefi/linux-lts-quantal-amd64/current/)


I'm so happy I could cry... backup time!!!

---

