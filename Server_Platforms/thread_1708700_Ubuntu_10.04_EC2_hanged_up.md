---
title: "Ubuntu 10.04 EC2 hanged up"
date: 2011-03-17
forum: Server Platforms
---

### Post by jeevandongre on 2011-03-17
I have created an instance of ubuntu 10.04 lucid lynx and now I tried to install apache tomcat6 on the instance.
the command I followed to create an instance on ubuntu is
sudo apt-get install tomcat6 
but the server seems to be hanged and I am not able to terminate the process

Setting up openjdk-6-jre-headless (6b20-1.9.7-0ubuntu1~10.04.1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/java to provide /usr/bin/java (java) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode.

---

### Post by BkkBonanza on 2011-03-17
Are you sure it's not just taking a while? You can usually use **Ctrl-C** to terminate. Also you should be able to ssh in again to open a new terminal and then use **ps afx** to see the other process and what state it's in.

---

### Post by jeevandongre on 2011-03-17
Ctrl-C was not working and I just restarted the server and I am not able to login to the server through ssh

---

### Post by BkkBonanza on 2011-03-17
If you're on a micro instance they used to have an issue with the Ubuntu images not rebooting correctly due to the "ephemeral" storage device not getting mounted at boot. I don't know if they fixed that or decided it was "as expected", but I know I had to manually fix mine for reboots to work.

What happens at boot is that a device gets mounted that isn't supported by the micro instances (that only work with EBS elastic block store). This device prevents the boot from continuing due to an error. The way I got around it was to mount the "dead" instance (root volume) as a secondary mount on another instance and go in and edit the /etc/fstab manually to not have that extra device mount at boot. Then unmount it and try to start it again. 

There is posts in the AWS forum about this. And as I said I'm not sure if they fixed it as it was months ago I last ran into this. It is a mistake (?) in the Ubuntu images that only shows up when booting as micro instance. Whenever I start with a new micro instance the first thing I do now is check the /etc/fstab and make there isn't an ephemeral store device line there.

I'll see if I can dig up something on google...

Edit: found it here:
[https://forums.aws.amazon.com/thread.jspa?threadID=51380](https://forums.aws.amazon.com/thread.jspa?threadID=51380)

a few ways posted there for fixing. If your instance is running or stopped then I'd go the way of mounting on another instance. If you already terminated it then you'll need to start again anyway.

Edit: there is also currently a post on fixing root volumes on the [Alestic.com]("http://alestic.com") site. Same basic idea there.

---

### Post by BkkBonanza on 2011-03-17
BTW I used the same idea to downsize the root volume on my instance. I think they start out at 10 GB, which costs around $1.50/mo. storage. I reduced mine to 1GB and it works fine with still enough free space.

Same idea, attach and mount the root volume on another instance, create a 1GB volume and attach, mount it. Then rsync all the root files over. Detach both and attach the root volume back to the original instance and start up again, now with a 1GB root volume. 90% savings, if you don't need the space, don't pay for it.

---

### Post by jeevandongre on 2011-03-17
> **BkkBonanza said:**
> BTW I used the same idea to downsize the root volume on my instance. I think they start out at 10 GB, which costs around $1.50/mo. storage. I reduced mine to 1GB and it works fine with still enough free space.

Same idea, attach and mount the root volume on another instance, create a 1GB volume and attach, mount it. Then rsync all the root files over. Detach both and attach the root volume back to the original instance and start up again, now with a 1GB root volume. 90% savings, if you don't need the space, don't pay for it.
Now I created an new instance, actually i am experimenting and i am novice to this ec2. Now I tried to install java6 jdk, I encountered the same error. And I am using AMI-6a3dcf03 instance of the ubuntu10.04 lucid lynx. I never tried the things which you mentioned in the above post. But I am struggling to do the things. I have a web app which was built using java servlets and mysql so I dont even known how to configure that.I would like to take your suggestions and guidance.

Thanks a lot

---

### Post by BkkBonanza on 2011-03-17
I'm not familiar with that AMI you noted above and it could be that it doesn't have the issue with micro instances.

But if it does my guess is that maybe the java6 install is at some point having trouble with the storage device that's missing. I can't be sure. 

After starting up a new instance I'd have a look in the /etc/fstab file right away and if there are two storage devices there then remove the line that is **NOT mounted at root** (/). It will cause failure on any later reboots. Then type the **mount** command to see if that same device is mounted (just in case) and if it is then umount it.

Then run **sudo apt-get update** and **sudo apt-get upgrade** to bring the system up to date with any fixes etc. 

Then try a reboot and see if that is successful for you. It should disconnect you and then after it's up again you can login again. This gives you a decent starting point.

Then try to do the java6 install again. I'm not a java/jsp user so I can't really say anything on that from experience. Maybe before doing that google "EC2 Ubuntu java6" to see if there are known issues out there. Hopefully after these baseline steps the prpblem will go away and it will complete the install. But certainly if there are known issues with java6 and EC2 then google ought to turn up some info.

---

### Post by jeevandongre on 2011-03-17
Thanks a lot for the help. let me try out the things and i have posted the same question on aws forms I will try it out I will get back to you. I am really sorry I am novice and newbie to this. Kindly help me to figure it out.

---

### Post by jeevandongre on 2011-03-27
Should I attach the volume to my instance explicitly or when ever I create an instance it will be attached by by default. How does it work and I have one more problem when I try to run ec2-api-tools commands I am getting an error saying --K private key not found. What it means. I am not able to either stop or terminate my instance from my console.

---

### Post by BkkBonanza on 2011-03-27
When you start a new instance it will have a volume attached (by default) and mounted at / (root). But to fix an instance with past problems (that won't boot) you would have to go through a manual detach/attach sequence. The main thing is to look at the /etc/fstab file to see what volumes are set to mount on booting.

Regarding ec2-api-tools I don't actually use them. I believe you need -k not --K but maybe this is just a typo here. I use the Tim Kay perl script which does the same thing but I find it easier to use. If the option is incorrectly set then it would not find the key file and probably give you that message.

If you don't have a good tutorial on that try [this one]("http://linuxsysadminblog.com/2009/06/howto-get-started-with-amazon-ec2-api-tools/") (from google). It seems to have the details.

---

### Post by jeevandongre on 2011-03-30
Let me come to the real problem now, I have a java/j2ee based web application. I have mysql 5.1 database running at the back end. I am working in a start up and we are launching beta this saturaday. we have developed on local machine, but now I want to move by database to RDS and we are saving  fews files on local hard disk. To save files I am planning to use s3 do we have to change any thing in design what is the procedure I need to follow, or else at least for the time being I can do that on my server itself and later I can move on to RDS and S3.

---

### Post by BkkBonanza on 2011-03-30
For serving files from S3 you would copy the files up to S3 and configure the"bucket" to be "public". Then you would want a CNAME record at your DNS server that points the suitable URL for those files to the correct address for the bucket.

eg. If you want your files at img.mydomain.net 

then you would configure a bucket named img.mydomain.net

and put the files in that bucket. Then add a CNAME record,

CNAME img.mydomain.net -> img.mydomain.net.s3.amazonaws.com

Now a link to img.mydomain.net/myphoto.jpg will find the file in the bucket actually at img.mydomain.net.s3.amazonaws.com/myphoto.jpg.

This isn't mandatory but it makes it so amazonaws doesn't show up in the url for users and allows you to switch file locations just by changing the DNS record. No need to edit the web site links programmed already.

I haven't used Amazon RDS yet. I've only done mysql on my own instance. But I'm sure it's fairly easy to move mysql data up to RDS. I recall seeing they have a how-to on their site. You can probably connect a local mysql client to the RDS server directly and pump the sql statements right into it. It may be safer as far as security to copy the mysql data to your ec2 instance and then use a mysql client to go into RDS directly from there.

---

### Post by jeevandongre on 2011-03-31
Okay fine, then I will run mysql5.1 in my instance only and FYI I am using micro instance, I am running on apache tomcat6 application server. Should I install apache2 web server also? How do I connect WAR file with mysql database and transact with them?

---

### Post by BkkBonanza on 2011-03-31
What is a WAR file? Not familiar with that.

---

### Post by jeevandongre on 2011-03-31
WAR file is packaged version of java application. All java based applications are deployed using Java War file.

---

### Post by BkkBonanza on 2011-03-31
Ah, I see. I can't help with the Java.
If it's similar to PHP you would have to configure the host, user, pwd to connect. If Mysql runs on the same instance then host is "localhost". If it's an RDS instance then you would config the IP of that instance.

---

### Post by jeevandongre on 2011-04-01
Hi I have created an amazon ec2 instance and now I need to deploy my java/j2ee based web app. I have apache tomcat6 running. I am managing the server via ssh in terminal. I need to copy war files to the server through how do I do that. I am newbie kindly help me

---

### Post by BkkBonanza on 2011-04-01
You can use sftp easily over ssh. Or rsync may be better.

From your local system (not at server via ssh, though you may also have one open):

**rsync -avz /path/to/src user@server:/path/to/dest**

sftp works similarly way but doesn't have as good differential copying when you are copying a file that was already copied and has changed. 

You can also use Nautilus to copy files using your gui, drag and drop. Just use a location specifier like ssh://user@server:/path/to/dest. It will open that location and you can drop files into it. It uses sftp transparently behind the scenes.

rsync is likely the most direct and useful way thogh as you can create a script to refresh remote server files with local updates and it will only copy changed portions of files. So for databases being updated it can be very fast.

---

### Post by jeevandongre on 2011-04-01
I tried rsync I used this command rsync -avz filename.war instance_key.pem [email]ubuntu@xx.xx.xxx.xx[/email]:/var/lib/tomcat6/webapps and I also tried rync -avz filename.war [email]ubuntu@xx.xx.xxx.xx[/email]:/var/lib/tomcat6/webapps from both remote terminal and local terminal but its not working I am getting an error which says permission denied (public key)

---

### Post by BkkBonanza on 2011-04-01
Ah yes, if you have a special identity file you need to add some options. But the easier way is to put the identity and user info in a config file and then it happens as normal for all ssh and rsync usage. I'd recommend this method.

Create a file ~.ssh/config and add these lines (modified to suit you):
```

Host *.compute-1.amazonaws.com
StrictHostKeyChecking no
UserKnownHostsFile .ssh/AWSHosts
IdentityFile .ssh/instance_key.pem
User ubuntu

```
Make sure the instance_key.pem is also in that directory or use a path to specify.

Now use ssh and rsync without user name  and identity options needed. This makes everything easier when connecting to EC2 (and also prevents everchanging host keys from polluting your knownhosts file).

**rsync -avz /file/to/src  server:/path/to/dest**

If you want to do it the harder way you need to adjust the cmd options like this,

**rsync -avz -e "ssh -i instance_key.pem" /path/to/src user@server:/path/to/dest**

They both do the same but the first makes use of defaults associated by the Host line in the config file. This also makes it easier for nautilus or any other program going over ssh.

Note also, the user you login as needs to have write permission on the dest directory.

---

### Post by jeevandongre on 2011-04-16
Thank you very much we finally hosted beta 001 version of our product,
check out beta001.joineventus.com, its a temp solution

---

### Post by bianbian on 2011-08-04
> **BkkBonanza said:**
> BTW I used the same idea to downsize the root volume on my instance. I think they start out at 10 GB, which costs around $1.50/mo. storage. I reduced mine to 1GB and it works fine with still enough free space.

Same idea, attach and mount the root volume on another instance, create a 1GB volume and attach, mount it. Then rsync all the root files over. Detach both and attach the root volume back to the original instance and start up again, now with a 1GB root volume. 90% savings, if you don't need the space, don't pay for it.

Hi BkkBonanza,
Could you plz tell me how did you do this?
I try as you said, but the new instance can't start at all..

---

