---
title: "Same ol' Linux"
date: 2009-09-19
forum: Testimonials &amp; Experiences
---

### Post by rcaldera43 on 2009-09-19
I've been away from any Linux OS for 8 years. I'm not fond of M$ Windows at all but it's so everywhere, it's hard not too use it. I've heard so much recently about the new user friendly Linux, especially Ubuntu so I thought I'd give it a retry. Sorry, but the frustration is still at the same level as before. I'm trying a simple install of vsftpd. I open up the terminal and it won't let me do anything that's 'su' related. It won't accept any password I give. Only once during my install of Ubuntu did it prompt me to pick a password so I put in something very simple; 111111. It won't recognize it. I have to admit, I was impressed during the install how it recognized all my hardware. Sound, wireless card, Ethernet... But these damn permissions in Linux are so UNuser friendly. I help people all the time with their Windows OS's but I honestly STILL can't recommend Linux.

---

### Post by sideaway on 2009-09-19
It won't accept your password because you have it wrong. Wrong number of 1's perhaps? Maybe you should try a password you can actually remember.

Never ever have I heard of a freshly installed Ubuntu 'refusing' a correctly entered password. It's always a case of PEBKAC.

Permissions are handled with chmod.

---

### Post by markusf21 on 2009-09-19
ubuntu uses sudo to escalate permissions

---

### Post by Lantesh on 2009-09-19
Linux is not Windows, so the first thing to accept is that there is going to be a learning curve.  It's not going to be easy to use until you put the time in.  I think you are frustrated because you want to be able to do all the things you do in Windows right away.  Unfortunately that is not realistic.  I've been using Linux for 2 1/2 years, and I'm still learning.  Put some time into it and you will be rewarded.

---

### Post by odinb on 2009-09-20
HowTo - VSFTPD with virtual users and mysql.

You do not need a system account on the machine to run FTP, this is ofcourse not needed, you can use virtual FTP-users instead.

Install the following on your machine:
- vsftpd server ( sudo apt-get install vsftpd )
- MySQL server ( see [http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4) and scroll to 13 mySQL and follow instructions.)


1a) Create a database for vsftpd:

Code: (copy and paste)
    mysql -u root -p


1b) Replace ftpdpass below with the pass you want for the user vsftpd. Please keep track of it, as you will need it later!

Code: (copy and paste)
    CREATE DATABASE vsftpd;
    GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON vsftpd.* TO 'vsftpd'@'localhost' IDENTIFIED BY 'ftpdpass';
    GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON vsftpd.* TO 'vsftpd'@'localhost.localdomain' IDENTIFIED BY 'ftpdpass';
    FLUSH PRIVILEGES;


Code: (copy and paste)
    USE vsftpd;


Code: (copy and paste)
    CREATE TABLE `accounts` (
    `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY ,
    `username` VARCHAR( 30 ) NOT NULL ,
    `pass` VARCHAR( 50 ) NOT NULL ,
    UNIQUE (
    `username`
    )
    ) ENGINE = MYISAM ;


Code: (copy and paste)
    quit;


2. Configure vsftpd.
2a) Create the user vsftpd, belonging to the group nogroup with the home folder /home/vsftpd. vsftpd will be run as this user.

Code: (copy and paste)
    useradd --home /home/vsftpd --gid nogroup -m --shell /bin/false vsftpd


2b) Create a new vsftpd.conf
Create a copy of the existing first, just in case...

Code: (copy and paste)
    cp /etc/vsftpd.conf /etc/vsftpd.conf_orginal


2c) Create an empty vsftpd.conf and open it.

Code: (copy and paste)
    cat /dev/null > /etc/vsftpd.conf
    nano /etc/vsftpd.conf


2d) Copy/paste the following and save:
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
pasv_min_port=50505
pasv_max_port=50510
nopriv_user=vsftpd
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
guest_enable=YES
guest_username=vsftpd
local_root=/home/vsftpd/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf

2e) Create a folder:

Code: (copy and paste)
    mkdir /etc/vsftpd_user_conf


In this folder you may save user-specific config files, but that is not covered here...


3. Configure PAM.
Now we will configure PAM to use MySQL to authenticate our virtual users. Make sure libpam-mysql is installed.

Code: (copy and paste)
    apt-get install libpam-mysql

3a) Copy the existing PAM Configuration for vsftpd

Code: (copy and paste)
    cp /etc/pam.d/vsftpd /etc/pam.d/vsftpd_orginal

3b) Create an empty file vsftpd and open it:

Code: (copy and paste)
    cat /dev/null > /etc/pam.d/vsftpd
    nano /etc/pam.d/vsftpd

3c) Copy/paste the following and save (CAUTION!! Replace ftpdpass with the earlier chosen pass I told you to remember!):
auth required pam_mysql.so user=vsftpd passwd=ftpdpass host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2
account required pam_mysql.so user=vsftpd passwd=ftpdpass host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2


4. Restart vsftpd:

Code: (copy and paste)
    /etc/init.d/vsftpd restart


5. Now create a virtual user (johndoe with the password mysecret)

Code: (copy and paste)
    mysql -u root -p

Code: (copy and paste)
    USE vsftpd;

Code: (copy and paste)
    INSERT INTO accounts (username, pass) VALUES('johndoe', PASSWORD('mysecret'));

Code: (copy and paste)
    quit;


We now also have to create a folder for the virtual user johndoe:

Code: (copy and paste)
    mkdir /home/vsftpd/johndoe
    chown vsftpd:nogroup /home/vsftpd/johndoe


Time to do a testrun with user johndoe!
Remember to open ports 21 and 50505-50510 in your firewall for incoming traffic to this machine if you have a firewall.

Good luck!

---

### Post by rcaldera43 on 2009-09-20
You make a good point about Linux not being Windows. I don't want it to be. I'm confident I'll be able to figure out what I've done wrong with my password. If not, I'll just reinstall the OS and be more vigilant. But I was hoping I'd be able to tell everyone I know to get away from Window$ and start using Linux. I've taken Unix classes and I like using terminal commands so the changeover won't be difficult for me but for the rest of the Window$ users I know...

---

### Post by Chronon on 2009-09-20
You can't use "su" unless you set up a root account.  This is not part of the scheme that Ubuntu operates under and by default there is no root account on an Ubuntu system.  As someone upthread said, you need to use "sudo" to temporarily escalate your user privileges.

---

### Post by 73ckn797 on 2009-09-20
> **Lantesh said:**
> Linux is not Windows, so the first thing to accept is that there is going to be a learning curve.  It's not going to be easy to use until you put the time in.  I think you are frustrated because you want to be able to do all the things you do in Windows right away.  Unfortunately that is not realistic.  I've been using Linux for 2 1/2 years, and I'm still learning.  Put some time into it and you will be rewarded.


+1
You got that shot right!

---

### Post by 3rdalbum on 2009-09-20
So, everything worked out-of-the-box for you, and the only issue you came across is that you need to use "sudo" instead of "su"? Sounds like Ubuntu has truly arrived.

Note: The average user will not be installing an FTP server on the command-line. Heck, I've never even wanted to do it.

---

### Post by HereInOz on 2009-09-20
I changed my 80 year old mother from a Windows environment to an Ubuntu environment.  Took me about two weeks before I stopped getting the phone calls.  Two weeks, and she is 80 years old and has had a stroke which has affected her memory.

Must be one tough to use OS, this Ubuntu.  Mind you, she didn't want to set up an FTP server either.

---

### Post by Chronon on 2009-09-20
> **Soley said:**
> Did you not read up on Ubuntu before you installed it? If you did you'd notice that it uses sudo & there is no root password/account. You can make one by typing ```
sudo passwd
```

Then you can su - to your hearts content.

OR skip that process and type ```
sudo -i
``` enter your password & you're in your root account.

You aren't supposed to give advice on how to enable the root account unless it's absolutely necessary for reasons given here: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Soley on 2009-09-20
> **Chronon said:**
> You aren't supposed to give advice on how to enable the root account unless it's absolutely necessary for reasons given here: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

I feel like that's taking away from the "freedom". Isn't that one of the bases Ubuntu is founded on?

Actually, nevermind. I just *really* read that thread. I'll be moving to Arch Linux now. So long Ubuntu!

---

### Post by mdsmedia on 2009-09-20
> **Soley said:**
> I feel like that's taking away from the "freedom". Isn't that one of the bases Ubuntu is founded on?

Actually, nevermind. I just *really* read that thread. I'll be moving to Arch Linux now. So long Ubuntu!
I have Arch installed on 2 of my computers, so don't take this the wrong way.

Why do you want to leave Ubuntu due to that thread? It is simply the policy of the forums not to undermine the security of ubuntu users. Where is the problem with that?

---

### Post by Tamlynmac on 2009-09-21
> mdsmedia
Why do you want to leave Ubuntu due to that thread? It is simply the policy of the forums not to undermine the security of ubuntu users. Where is the problem with that?

Do you honestly believe that's why or is it possible theres a different motive for that post???


> 
[rcaldera43]("http://ubuntuforums.org/member.php?u=915569")
But these damn permissions in Linux are so UNuser friendly. I help people all the time with their Windows OS's but I honestly STILL can't recommend Linux.

:shock:
Have no doubt this will result in a 10% reduction in new Ubuntu/Linux users this year alone. Guess you'd better stay in the Windows environment, as it appears your comfortable there.

Good Luck

---

### Post by Hallvor on 2009-09-21
> **Chronon said:**
> You aren't supposed to give advice on how to enable the root account unless it's absolutely necessary for reasons given here: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Su in a shell is not the same as graphically logging in as root. There is nothing wrong with the former, but the latter is sheer stupidity.

---

### Post by snowpine on 2009-09-21
> **rcaldera43 said:**
> You make a good point about Linux not being Windows. I don't want it to be. I'm confident I'll be able to figure out what I've done wrong with my password. If not, I'll just reinstall the OS and be more vigilant. But I was hoping I'd be able to tell everyone I know to get away from Window$ and start using Linux. I've taken Unix classes and I like using terminal commands so the changeover won't be difficult for me but for the rest of the Window$ users I know...

So basically you want to switch to Linux so you can feel superior to your friends? Arch should be perfect for you. :)

---

### Post by Hallvor on 2009-09-21
> **snowpine said:**
> So basically you want to switch to Linux so you can feel superior to your friends? Arch should be perfect for you. :)

What is wrong with Gentoo, Slackware or LFS? :)

---

### Post by Perfect Storm on 2009-09-21
The thread is closed as OP said his goodbye.

---

