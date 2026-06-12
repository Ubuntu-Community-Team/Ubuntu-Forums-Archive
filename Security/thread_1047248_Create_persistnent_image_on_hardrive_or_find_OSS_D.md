---
title: "Create persistnent image on hardrive or find OSS Deep Freeze Solution"
date: 2009-01-22
forum: Security
---

### Post by Mindslant on 2009-01-22
I run a 27 system lab for a school K-8th and all my computers just got replaced so I need to re-install Ubuntu.  Kindergartners continiously accidentally delete desktop icons or make new folders, the higher grade levels are just malicious.  

Deep freeze was installed on the windows partition and I'm impressed with the ability to still install new programs when I need to and still lock out permanent changes by students. 

What is the best option for Ubuntu?

Thankyou,
Mindslant

---

### Post by cdenley on 2009-01-22
[http://ubuntuforums.org/showpost.php?p=5720661&postcount=5](http://ubuntuforums.org/showpost.php?p=5720661&postcount=5)
This solution basically turns your entire filesystem into a livecd. All changes to the filesystem are stored in memory, and the actual filesystem isn't touched. When rebooted, all changes are rolled back. This solution may increase your memory requirements, and makes administration tasks such as installing updates a real pain.

---

### Post by Mindslant on 2009-01-22
Okay,I get the concept.  I wonder though, If I do want change something, how would I? Thats one of the deep freeze features I need.

---

### Post by cdenley on 2009-01-22
> **Mindslant said:**
> Okay,I get the concept.  I wonder though, If I do want change something, how would I? Thats one of the deep freeze features I need.

Boot to a livecd, mount the filesystem normally, then either make the changes from there, or disable the aufs script and reconstruct initramfs.

---

### Post by cdenley on 2009-01-22
If you want all users to start with a fresh home directory every time the computer boots, delete everything in /home, mount /home as tmpfs, then add this line to /etc/pam.d/common-session.
```

session required pam_mkhomedir.so skel=/etc/skel/

```
If you want some users to have home directories which they can change (such as admins), put it somewhere outside of /home. Regular users shouldn't be able to change anything outside of their home directory, and you will still be able to change system settings and install updates, so this may be a better solution.

---

### Post by Mindslant on 2009-01-22
Example:  I put the GCopmris icon on the desktop for Kindergarteners.  They acidentally delete the icon.  I restart and the icon pops back.  

An eigth grader needs Audacity to mix music for a project.  In the admin account I install it and make it available to all users.  When the eigth grader logs in he can use the program.


Will this solution do that?  

I appreciate all your help with this by the way, making my life so much easier.

---

### Post by cdenley on 2009-01-22
> **Mindslant said:**
> Example:  I put the GCopmris icon on the desktop for Kindergarteners.  They acidentally delete the icon.  I restart and the icon pops back.  

An eigth grader needs Audacity to mix music for a project.  In the admin account I install it and make it available to all users.  When the eigth grader logs in he can use the program.


Will this solution do that?  

I appreciate all your help with this by the way, making my life so much easier.

Using tmpfs for /home will do that, except any Desktop icons need to be in /etc/skel/Desktop.

---

### Post by Mindslant on 2009-01-22
Thank you, I will try this tomorrow morning.  I greatly appreciate your help.

---

### Post by Mindslant on 2009-01-22
I was hoping not to have to ask point blank.  I'm not too confident in my ability to write the script for mounting /home to tmpfs.  I found these two websites:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux)

[http://docs.sun.com/app/docs/doc/817-5093/6mkisoqdh?a=view](http://docs.sun.com/app/docs/doc/817-5093/6mkisoqdh?a=view)

I think the steps might look like:

1.  delete everything in /home

2.  Mount /home to tmpfs
# mkdir /home
# chmod 777 /home
# mount -F tmpfs -o size=50m swap /home
# mount -v

3.  Add  session required pam_mkhomedir.so skel=/etc/skel/ to /etc/pam.d/common-session

4.  Put Admin home directories anywhere but /home (I'm not sure how to do this exaclty)

5.  Put Desktop icons in /etc/skel/Desktop

The effect is that non-root users are 'blank' at ever boot but Admin can perform permanent changes such as updates.

It that about right?

Also without looking I don't know what the 777 bit is about.

Thankyou.

---

### Post by jcsteele on 2009-01-23
I manage a 20+ ubuntu lab (converted from XP) and we have had great success with getting students using Ubuntu - we use a simple setup (KISS) in which the users have full reign over their /home/user directory - they can write to anywhere they want, delete anything they want, mess everything up.  However, the computers are rebooted regularly (multiple times per day) and during a reboot, the workstation restores the /home/user directory from a simple tar.gz file that was created previously.  Below is the shell script we use upon reboot...
```

if [ -f /psso/psychlab.tar.gz ]; then
    cp /psso/psychlab.tar.gz /home/
    rm -rf /home/psychlab
    cd /home
    tar -xvzf psychlab.tar.gz
    echo "Remote Archive Restore Success!  Workstation Restore is complete!"
    exit 0
else
    echo "FAILURE!  Cannot find profile archive."
    exit 1
fi  
```

All of the machines have the same username/password to login, and all are fairly identical (Older Dell's - P4 2.0ghz 2.0GB Ram 40GB HDD) so basically when they reboot we are setting them back to "default" in the way we want them - this DOES NOT protect the system areas from compromise, however with the unix permission systems setup, we have been running for about a year with zero problems.  All machines have two accounts, "psychlab" which is for the users - a non-privledged user, and "psychadmin" which is an administrative user.

We have one machine setup as an administrative machine - its just another workstation, nothing special, which psychadmin and psychlab accounts as well, just not accessible by anyone - I can login to the psychlab account, change a desktop icon, create a shortcut, upload a HOWTO document, etc. (anything that I want done) - then I simply logout and "rebuild" the psychlab profile with this script, which is ran at boot time:

```
if [ $(id -u) != "0" ]; then
    echo "You must run this script as a superuser!"
    exit 1
fi

if [ -f /home/psychlab.tar.gz ]; then
    rm /home/psychlab.tar.gz
fi
    if [ -d /home/psychlab ]; then
        cd /home
        tar -cpPf psychlab.tar psychlab
    gzip psychlab.tar
      echo "Success!  You have built the psychlab profile archive!"
    if [ -f /home/psychlab.tar.gz ]; then
        cp /home/psychlab.tar.gz /psso/psychlab.tar.gz
        echo " "
        echo "Success!"
        echo "Reboot the workstations to propagate the changes"
    else
        echo "Cannot find file...something very bad has happened."
        exit 1
        fi
        exit 0
    else
        echo "Yikes! I cannot find the psychlab directory!"
        exit 1
    fi
    
fi  
```

The only nuisance I have found is that I have to manually go into the /home/psychlab directory and remove the .openoffice directory because OOorg doesn't like the different hostnames on the workstations - not a big deal really - I just haven't scripted this step yet (I am lazy)...

After we have a /psso/psychlab.tar.gz profile build - we simply use scp to copy the newly build profile to all the workstations like below:

```
scp -o StrictHostKeyChecking=no /psso/psychlab.tar.gz psso-ws01:/psso/
```

We use public key authentication between the admin workstation and the user workstations - so this process runs quickly.  After we have the newly built profile in /psso/psychlab.tar.gz of every workstation a simple reboot will update the workstations to use the new profile:

```
ssh -o StrictHostKeyChecking=no psso-ws01 'sudo reboot'
```

Rebooting all the stations is actually a neat experience - we get a PC Beep from every workstation in sequence as the script gets executed down the line - the machines are arranged in a circle around the admin machine, so its sort of a 3D bee buzzing experience :-)

As for software updates, etc. we simply user apt-cacher which makes all the user workstations pull their updates from the admin workstation - this is fairly well documented, etc. and makes things both quick, saves A LOT of bandwidth, and allows me to try out new updates on the admin workstation before they get put on the user workstations.

Anyways, this is really long - if you have any questions I would be glad to help - I searched forever before we started this project with the exact reasons you have, and didn't find anything, so I had to come up with this - it's not perfect, but it works for our needs...I been meaning to do put this in more detail on my blog, but like i said, I am lazy and haven't found the time - maybe I will this weekend though since this has spiked my interest.

Hope this helps,

JCS

---

### Post by Mindslant on 2009-01-23
jcsteele, 
because I don't have access to the server I'm leary relying on it. That is why I've pursued a stand-alone solution.

Thank you so much though.  If IT gets turned over to me this is definitely the way I want to go.  It sounds much easier.

---

### Post by Mindslant on 2009-01-23
> 
I think the steps might look like:

1.  delete everything in /home

2.  Mount /home to tmpfs
# mkdir /home
# chmod 777 /home
# mount -F tmpfs -o size=50m swap /home
# mount -v

3.  Add  "session required pam_mkhomedir.so skel=/etc/skel/" to /etc/pam.d/common-session

4.  Put Admin home directories anywhere but /home (I'm not sure how to do this exaclty)

5.  Put Desktop icons in /etc/skel/Desktop


I think I got 4 figured out.  "adduser -d /homeadmin" should work right?

---

### Post by jcsteele on 2009-01-24
> **Mindslant said:**
> jcsteele, 
because I don't have access to the server I'm leary relying on it. That is why I've pursued a stand-alone solution.

Thank you so much though.  If IT gets turned over to me this is definitely the way I want to go.  It sounds much easier.

Well, you really don't need to use a stand-alone server - any of the workstations will work fine - you just need to build the profile on that workstation and distribute it to all the other machines.  The reason I choose this solution in the first place is because the workstations are not reliant on any type of server really - the server can be powered off for long periods of time, and the workstations still function flawlessly, which is better than using some sort of dumb terminal solution or NFS exported directories to manage things. After everything was setup and functioning I went and started to use apt-cacher for updates, and then I just "borrowed" one of the workstations - it's not really a server at all (all machines run Ubuntu 8.04 Desktop - including our "server") but you really don't need to use apt-cacher if you don't want too, but it does make things quicker and easier to manage.

JCS

---

