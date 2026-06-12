---
title: "subprocess new pre-removal script returned error exit status 102"
date: 2006-08-21
forum: Repositories &amp; Backports
---

### Post by Sebata_Afrika on 2006-08-21
Hi all

Please help with this error. This is the message I got after running 'sudo apt-get -f install'

invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Some of the attempts I did to remove this include a solution from MikeBee:
Once I removed '/etc/rc2.d/samba' and '/etc/rc3.d/samba' links are relinked them both to '../init.d/samba' by 'sudo ln -s ../init.d/samba /etc/rc2.d/samba' and 'sudo ln -s ../init.d/samba /etc/rc3.d/samba' then ran 'sudo apt-get -f install' it worked fine.

But this did not work for me at all!

any ideas?

---

### Post by Sebata_Afrika on 2006-08-21
I also tried this 'sudo apt-get build-dep samba' and got the error:
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

then did this 'sudo apt-get -f install samba' and it then trew me back with:
subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm running out of ideas

Tshepo...........

---

### Post by Sebata_Afrika on 2006-08-22
Seems like Rudi (a colleague) helped me solve the problem, here are the steps.
- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found  K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba
- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.

---

### Post by tjansson on 2006-10-26
I had the same problem after my upgrade, and the advice from Sebata_Afrika helped! :D thx

---

### Post by phoenix_1983 on 2006-11-03
Thanks for the how to.. this got me back up an running :P

---

### Post by halitus87 on 2006-11-04
yay i have been having problems with this for a while  thanky ou very much

---

### Post by alh84001 on 2006-11-21
One more happy ubuntu user here. Tnx.

---

### Post by jory on 2006-12-15
hi,

i had the same problem when i upgraded ubuntu. your solution helped me very well, it's not even necessary to do it in the order you suggested. all you have to do:

cd /etc/rc2.d
sudo rm S91samba
sudo ln -s ../init.d/samba S91samba
sudo apt-get -f install

and that's it...

jonas

---

### Post by anaspeople on 2006-12-16
Thanks a lot! I had the same problem and now everything working:D

---

### Post by mdonahoe on 2007-01-05
Thanks, this really helped me.  This is the reason Ubuntu is so amazing.

---

### Post by leona on 2007-02-06
Thank you that solved my problem too, didn't have the S directory I had the K but once removed it reinstalled fine.
Mine seemed to break after today's update :(

---

### Post by zucca on 2007-02-07
I just had the same problems and fixed it as suggested (under dapper)

---

### Post by fritz_monroe on 2007-02-07
I'll add in my thanks.  I did the auto upgrade today and it errored out.  Thanks to the step by step here, I'm up and running.

---

### Post by John Jason Jordan on 2007-02-09
> **Sebata_Afrika said:**
> Seems like Rudi (a colleague) helped me solve the problem
Thanks to you and Rudi! Fixed the problem!

---

### Post by MarseHole on 2007-02-10
Thanks very much :D 
I was having the same problem, but the fix worked a treat.

Long live the Ubuntu Community!

---

### Post by muj0 on 2007-02-12
> **Sebata_Afrika said:**
> Seems like Rudi (a colleague) helped me solve the problem, here are the steps.
- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found  K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba
- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.

This did not work for me.

In fact, I do not have K09samba or S91samba in /etc/rc2.d (or /etc/rc3.d) I have S20samba
I tried the above using S20samba and I still got this error:

Setting up samba (3.0.22-1ubuntu4.1) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ideas?

---

### Post by looping_richard on 2007-02-21
Thanks to Rudi for pointing in the right direction!

I did this (I try to get things done WITHOUT going to terminal...):

Open /etc/rc2.d/ with root-nautilus-here in File Browser (it is under RightClick->Scripts)
Delete the file K09samba

Then in Synaptic Package Manager I marked Samba for "complete removal" and let it be removed.
Then in Synaptic: "Edit" -> "Reload Package information" 
Install went smooth this time.

Samba working.

Richard.

---

### Post by alan yeates on 2007-02-22
> **jory said:**
> hi,

i had the same problem when i upgraded ubuntu. your solution helped me very well, it's not even necessary to do it in the order you suggested. all you have to do:

cd /etc/rc2.d
sudo rm S91samba
sudo ln -s ../init.d/samba S91samba
sudo apt-get -f install

and that's it...

jonas
None of the above seems to work for me, I terminate with the same 102 error all the time (Ubuntu 6.06)

---

### Post by muj0 on 2007-03-09
I finally solved it. I just upgraded to 7.04 and now it works fine :)

---

### Post by CELI-Nux on 2007-05-19
Great !!!  Did the job for me too.  Don't forget to apply the procedure in both /etc/rc2.d AND /etc/rc3.d.  I did this with under root credentials (sudo su) and everything went smoooooothly :)

Viva Ubuntu Dapper 6.06 and the community.

Cheers

---

### Post by Fevrin on 2008-08-16
In case none of the above solutions help, I found that creating a new smb.conf file (in the absence of one) helps.  I found someone else who had this problem <http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-07/msg00617.html>, and they were suggested to reinstall samba-common.  Well, in the process of reinstalling that, it too gave me an error, but this error mentioned the fact that there was no smb.conf file (I had just deleted it in hopes that reinstalling samba would generate a new copy of the file), so I just typed into a terminal "sudo touch /etc/samba/smb.conf", and both samba-common and samba reinstalled successfully.  I don't know why they panicked without the smb.conf file, but I'm glad that the problem is solved.  Now, getting samba to *work* on the other hand . . .

---

### Post by anil_robo on 2008-11-02
I messed up a lot with samba.conf to setup an HDD as a network storage for myself and my roommate. It finally worked, but the process that got me there was very messy. So I thought of "wiping the slate clean" and uninstalled Samba using Synaptic. I also removed teh /etc/samba/ directory (along with the configuration files in there). When I tried to reinstall Samba, it kept givng me "Subprocess Post-Installation Script Returned Error, Exit Status" error.

The solution mentioned by Fevrin above worked. **I created a blank /etc/samba/smb.conf** and then Samba reinstalled like a breeze. Hope it helps someone.

On the other hand, I also think it's a bug. In case /etc/samba/smb.conf doesn't exist, shouldn't Samba install be able to create one?

---

