---
title: "iscsi mounting problems with openiscsi"
date: 2011-12-17
forum: Server Platforms
---

### Post by kanu2k11 on 2011-12-17
Hello Guys,
I am new to this forum and also a bit novice in ubuntu. But as my company has started to use ubuntu servers instead of windows which I like but facing some problems.
But right now the main problem is about the iscsi mounting.
We have a Dell Equallogic in which I have created 2 volumes to be mounted on our Ubuntu server 11.10. There is no problem in discovering and mounting them but one big problem that is When the server is rebooted or iscsi services are restarted the drives gets other drive name and hence does not mount properly.

Explanation is drive 1 get SDD1 and is mounted in /home/drive1 and drive 2 gets SDE1 and is mounted in /home/drive2 but when the iscsi service is restarted the mounts are there but the drives gets different drive letter. Drive 1 gets SDF1 and Drive 2 gets SDG1 as shown by FDISK -L command and Mount command still shows sdd and sde mounted but no data in it which is in my SAN drives.
So very confused about this, if someone can tell me how to get these drives mounted to sdd and sde respectively again even after a restart.
Please Help.
I have few more problems which I will ask in other threads.
Any Help is appreciated.
Thank You

---

### Post by TheR on 2011-12-18
This is how I did it. Look at this thread. [http://ubuntuforums.org/showthread.php?t=1578087](http://ubuntuforums.org/showthread.php?t=1578087)

by
TheR

---

### Post by kanu2k11 on 2011-12-19
> **TheR said:**
> This is how I did it. Look at this thread. [http://ubuntuforums.org/showthread.php?t=1578087](http://ubuntuforums.org/showthread.php?t=1578087)

by
TheR

Thanks for the link will try it today. :)

---

### Post by kanu2k11 on 2011-12-19
I tried but it didnt work :(
please help.
I installed ruby also. I am not too much into ruby or shell scripting so I might have done something wrong.

The openiscsi discovery shows the following drives which i need to mount:
172.16.1.100:3260,1 iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static
172.16.1.100:3260,1 iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ede6-scripts

Following is what I did according to what you wrote in that post:

1) did exactly the same thing at the exact location
2) for persistent.names.conf I entered 
iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static;10;iscsi/static
iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ede6-scripts;11;iscsi/scripts
3) installed ruby and created the exact ruby script

[RUBY]
#!/usr/bin/ruby
#parameter : ip-172.16.1.100:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static-lun-10
device = nil
# parse parm on - sign
a = ARGV.first.split('-')
# third element should be iscsi
exit 1 unless a[2] == 'iscsi'
# set iqn and lun
id_iqn = a[3] + '-' + a[4]
id_lun = a[6]
# read my configuration file /etc/iscsi/persistent.names.conf
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
# config line looks like this: iqn.2100-05.si.ozs:diski.sas;2;iscsi/dns1
iqn, lun, dev = line.chomp.split(';')
if iqn == id_iqn and lun == id_lun
device = dev
break
end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device
[/RUBY]



# is a comment so change in that does not matter i guess?

So where might be the problem? Any Ideas?
Please help.

---

### Post by kanu2k11 on 2011-12-20
TheR please help..

---

### Post by rubylaser on 2011-12-20
Those directions look like they should work. Do you have iscsi path target?  That script is depending on that or it breaks.

I've always just done ISCSI initiators and targets like [this]("http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target").  I haven't tested this on 11.10, but it works through 10.10 for me.  I'm still baffled why people are using the Server releases and not sticking to the Long Term Service releases. 10.04 is rock solid.

---

### Post by kanu2k11 on 2011-12-22
it was my mistake of using the 11.10 version for ubuntu I didnt see the 10.04 LTS version before downloading and now that I have already setup many things in the those two UBUNTU server so dont want to reformat them and install the 10.04 version. is there a way that I can downgrade to that LTS version without loosing any configuration??

Ok for the iSCSI thing. where can I find that iscsi path? Sorry if this is a stupid question i am just new to this storage thing and really want to learn.
I am trying to find the names now and will post when i get those. till then if you can just tell me where to find it?

---

### Post by kanu2k11 on 2011-12-22
isint "iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static" a target path??
or is there a difference between target path and path target?

"iqn.1993-08.org.debian:01:9a8a8f636440" is the initiator path

----
just to tell that I have noticed that under /dev there is no iscsi path available i.e. /dev/iscsi does not exist.

---

### Post by rubylaser on 2011-12-22
> **kanu2k11 said:**
> it was my mistake of using the 11.10 version for ubuntu I didnt see the 10.04 LTS version before downloading and now that I have already setup many things in the those two UBUNTU server so dont want to reformat them and install the 10.04 version. is there a way that I can downgrade to that LTS version without loosing any configuration??

Ok for the iSCSI thing. where can I find that iscsi path? Sorry if this is a stupid question i am just new to this storage thing and really want to learn.
I am trying to find the names now and will post when i get those. till then if you can just tell me where to find it?

Downgrading really isn't a good idea.  If you feel like you've got a lot of configuration invested in your server at this point, you might as well stay there.  I'll take a shot in a little bit at setting this up in Virtualbox on 11.10 Server.

---

### Post by rubylaser on 2011-12-22
> **kanu2k11 said:**
> isint "iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static" a target path??
or is there a difference between target path and path target?

"iqn.1993-08.org.debian:01:9a8a8f636440" is the initiator path

----
just to tell that I have noticed that under /dev there is no iscsi path available i.e. /dev/iscsi does not exist.

The directions I posted from [Howtoforge]("http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target") still work great on 11.10.  I setup two separate base installs of 11.10 64 bit server installs.  With one as the target an one as the initiator.  Some of the paths have changed in the newer versions of Ubuntu, but the concepts are still the same.  Here's what I did to get it working.

**Target**
On the target, I'm going to use /dev/sdb as a Logical Volume.
```
sudo -i
```

Install the packages.
```
apt-get install lvm2 iscsitarget iscsitarget-dkms
```
```
nano /etc/default/iscsitarget
```
... and set ISCSITARGET_ENABLE to **true**

Next, I'll setup the logical volume just like the tutorial.
```
fdisk /dev/sdb
```
```
pvcreate /dev/sdb1
```
```
vgcreate vg0 /dev/sdb1
```
```
lvcreate --name storage_lun1 --size 200M vg0
```
^ This is just a tiny 200 MB test volume, obviously make this much larger :)
```
 > /etc/iet/ietd.conf
```
```
nano /etc/iet/ietd.conf
```
And paste in your configuration.
```
Target iqn.2001-04.com.example:storage.lun1
        IncomingUser someuser secret
        OutgoingUser
        Lun 0 Path=/dev/vg0/storage_lun1,Type=fileio
        Alias LUN1
        #MaxConnections  6
```

```
nano /etc/iet/initiators.allow
```
and paste in your line.
```
iqn.2001-04.com.example:storage.lun1 10.1.1.212
```
Finally, start the target.
```
/etc/init.d/iscsitarget start
```

**Initiator**
```
apt-get install open-iscsi
```
```
nano /etc/iscsi/iscsid.conf
```
... and set node.startup to automatic:
```
[...]
node.startup = automatic
[...]
```

```
/etc/init.d/open-iscsi restart
```
Now, we can see what our target has to offer.
```
root@initiator:/storage# iscsiadm -m discovery -t st -p 10.1.1.210
10.1.1.210:3260,1 iqn.2001-04.com.example:storage.lun1
```

```
iscsiadm -m node --targetname "iqn.2001-04.com.example:storage.lun1" --portal "10.1.1.210:3260" --op=update --name node.session.auth.authmethod --value=CHAP
iscsiadm -m node --targetname "iqn.2001-04.com.example:storage.lun1" --portal "10.1.1.210:3260" --op=update --name node.session.auth.username --value=someuser
iscsiadm -m node --targetname "iqn.2001-04.com.example:storage.lun1" --portal "10.1.1.210:3260" --op=update --name node.session.auth.password --value=secret
```
^ Obviously adjust these to your setup.

Now, you can login like this.
```
iscsiadm -m node --targetname "iqn.2001-04.com.example:storage.lun1" --portal "10.1.1.210:3260" --login
```
Your ISCSI target should now show up in fdisk -l
```
fdisk -l
```

Add a partition with fdisk
```
fdisk /dev/sdb
```

Add a filesystem...
```
mkfs.ext4 /dev/sdb1
```

Make a place for it to mount.
```
mkdir /storage
```

Set it up to mount at boot.
```
nano /etc/fstab
```
Add this to the bottom.
```
/dev/sdb1       /storage        ext4    defaults,auto,_netdev 0 0
```

Finally, reboot and everything should be working as intended.

---

### Post by kanu2k11 on 2011-12-22
Thanks mate but i think i got you confused...
I just mentioned 2 linux machines just coz of the version as one ubuntu is using Dell SAN Equallogic as iSCSI target and the other ubuntu is a standalone and does not have anything to do with iscsi mounting...
Sorry..

for the initiator part I did exactly as you just mentioned but the the problem arises with multiple mounts. as when rebooting the iscsi volumes get the next available drive names and not the last one as mount is performed first and then the iscsi services are started so thats why volumes gets following names. 
eg. /dev/sdd1 for xyz drive and /dev/sde1 for abc drive after reboot /dev/sdd1 and sde1 remains mounted but when iscsi initiator services are started they see sdd1 and sde1 as used drives so xyz drive gets /dev/sdf1 and abc gets /dev/sdg1 so in effect they are actually not mounted. So i need to maintain some persistent names for these xyz and abc drives so that even after reboot they remain mounted with the same drive letter and not the next one. the script given by TheR should work but its not for me dont knw whats wrong... 
Hope you have understood the exact problem.

---

### Post by rubylaser on 2011-12-22
Your ISCSI mounts will each have a UUID, you can see what they are when you have them mounted by running
```
blkid
```

You'd just need to get those UUID's and then add them to /etc/fstab as UUIDs rather than device names.  Take a look at /etc/fstab for the syntax to add new lines.

---

### Post by kanu2k11 on 2011-12-22
got the UUIDs and my fstab looks like below

> UUID=cd935960-b3a6-4e21-a1a4-6572444c021f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba3a7851-ce43-4741-acdb-226f882ace2d none            swap    sw              0       0

/dev/sdd1       /home/storage1       ext4    defaults,auto,_netdev 0 0


/dev/sde1  /home/storage2  ext4  defaults  0  0


so where do you think I should add those
my UUIDs for the volumes are as below:

> /dev/sdd1: UUID="3f4cd254-d625-44a4-856c-65a4efb4e5c2" TYPE="ext4"
/dev/sde1: UUID="0ce0f991-5b6f-4ee4-bc7d-e1d42e0790af" TYPE="ext4"

Thanks mate

---

### Post by kanu2k11 on 2011-12-22
Complete Fstab file
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cd935960-b3a6-4e21-a1a4-6572444c021f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba3a7851-ce43-4741-acdb-226f882ace2d none            swap    sw              0       0

/dev/sdd1       /home/storage1       ext4    defaults,auto,_netdev 0 0


/dev/sde1  /home/storage2  ext4  defaults  0  0


---

### Post by rubylaser on 2011-12-22
Looks good, but you'd want to use the UUID's in the fstab rather than the devices.  Like this...
```

UUID=3f4cd254-d625-44a4-856c-65a4efb4e5c2 /home/storage1 ext4 defaults,auto,_netdev 0 0
UUID=0ce0f991-5b6f-4ee4-bc7d-e1d42e0790af /home/storage2 ext4 defaults 0 0

```

---

### Post by kanu2k11 on 2011-12-22
just did that damn it didnt worked should I have removed those persistent rules TheR told me to create???

---

### Post by rubylaser on 2011-12-22
They shouldn't be necessary if you followed my directions.  But, you'll likely need to run this after switching to UUIDs
```
update-initramfs -u
```
That should make the system use the UUIDs.  [This Ubuntu wiki doc]("https://help.ubuntu.com/community/UsingUUID") covers UUIDs.

---

### Post by kanu2k11 on 2011-12-22
Nope mate didnt work. :(
I check all your steps and i did the same thing and they are listed under fdisk -l but with the next drive name.....
What can be done now??

---

### Post by rubylaser on 2011-12-22
Are the UUID's remaining the same?  If so, UUID mounting should work just fine.  If it's not working, the only other guess I could make is that it's trying to mount the target before the open-iscsi service has started or the share is available.  You could write an init script to mount the shares at the end of the boot process.

---

### Post by kanu2k11 on 2011-12-22
yup just checked they are still the same...

I guess that is the only option left ... any help in that mate?

---

### Post by rubylaser on 2011-12-22
Sure, but first, after the system is booted and at a command prompt, does ```
mount -a
``` mount the shares for you or throw an error?

---

### Post by kanu2k11 on 2011-12-22
I just restarted the server and now its not accessible. Damn I need to go tomorrow to the datacenter to get that server up again.

---

### Post by rubylaser on 2011-12-22
I'm guessing that it's sitting at a prompt saying that your mountpoint is not available, would you like to press "S" to skip.

---

### Post by kanu2k11 on 2011-12-22
its strange I am able to ping that server but not SSH into it suddenly...
not even from another local server.

---

### Post by kanu2k11 on 2011-12-22
oh is it i'll see if i can get anyone to do that for me... will this happen at every restart???

---

### Post by kanu2k11 on 2011-12-22
I just got to know that there are some errors on the screen. some permission errors and the keyboard is not working so i will go tomorrow morning.

---

### Post by TheR on 2011-12-22
Sorry I am late to the party. I usually follow forum once a week.

There are some things that I might forget to explicitly mention. 

First is that ruby program file should have execute attribute on. Second is that once you restarted server or run iscsiadmin command, you have to restart client machine if you have done any changes to programs.

I would also check if ruby program gets started at all. You may put line:

File.open('/home/myusrdir/test.tst') {|f| f.write('running') }

somewhere at the beginning of program in order to debug if it works. If it works you should have file /home/myusrdir/test.tst present in your system.

by
TheR

---

### Post by TheR on 2011-12-22
I have read again your post and I see that your device name is somehow different than mine. So if we predict that you have only one iscsi server and that anything that meters is lun number, which is last number in parameter, ruby program may look like this.

#!/usr/bin/ruby
device = nil
id_lun = ARGV.first.split('-').last
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
  iqn, lun, dev = line.chomp.split(';')
  if lun == id_lun
    device = dev
    break
  end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device


by 
TheR

---

### Post by kanu2k11 on 2011-12-28
Sorry for coming back late got busy with other thing..
So problem still exists..
> I have read again your post and I see that your device name is somehow different than mine. So if we predict that you have only one iscsi server and that anything that meters is lun number, which is last number in parameter, ruby program may look like this.
I have one iSCSI server with two volumes for this ubuntu machine.
below is the device name so you think "6" would be the LUN no.????
> iqn.2001-05.com.equallogic\:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static

also I saw the errors they were as below in the pics during bootup.
[[IMG]http://img836.imageshack.us/img836/954/mountingerror1.th.jpg[/IMG]](http://imageshack.us/photo/my-images/836/mountingerror1.jpg/)
remaining screen
[[IMG]http://img51.imageshack.us/img51/9269/mountingerrorremainings.th.jpg[/IMG]](http://imageshack.us/photo/my-images/51/mountingerrorremainings.jpg/)

So now i'm going to check the script again.
but tell me do I need to restart the whole server to check if its working or just restarting iscsi services will be enough as i dont want it to be stuck at the same place again as last time.
P.S. i have changed the fstab file back to the old one and not using UUID to mount.

---

### Post by kanu2k11 on 2011-12-28
> **rubylaser said:**
> Sure, but first, after the system is booted and at a command prompt, does ```
mount -a
``` mount the shares for you or throw an error?

mount -a is not giving any problem and mounting fine.

---

### Post by kanu2k11 on 2011-12-28
> **TheR said:**
> Sorry I am late to the party. I usually follow forum once a week.

There are some things that I might forget to explicitly mention. 

First is that ruby program file should have execute attribute on. Second is that once you restarted server or run iscsiadmin command, you have to restart client machine if you have done any changes to programs.

I would also check if ruby program gets started at all. You may put line:

File.open('/home/myusrdir/test.tst') {|f| f.write('running') }

somewhere at the beginning of program in order to debug if it works. If it works you should have file /home/myusrdir/test.tst present in your system.

by
TheR

Where do you want me to do this?
I am currently doing everything on the client as the server is an Dell Equallogic box and does not have capability to run a OS or any custom program.
Ruby is installed in my client ubuntu machine.

---

### Post by rubylaser on 2011-12-28
You would add that command on the client to the Ruby script from the first page.  I'd change it to this though.

```
File.open('~/test.tst') {|f| f.write('running') }
```

Once the script has run, you should see running in the file if you cat it.

```
cat ~/test.tst
```

---

### Post by kanu2k11 on 2011-12-28
you mean the iscsi ruby script?

---

### Post by rubylaser on 2011-12-28
yup :)

Like this...
```

#!/usr/bin/ruby
device = nil
File.open('~/test.tst') {|f| f.write('running') }
id_lun = ARGV.first.split('-').last
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
iqn, lun, dev = line.chomp.split(';')
  if lun == id_lun
    device = dev
    break
  end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device

```

---

### Post by kanu2k11 on 2011-12-28
and do i need to restart the server in order to run the script or is there another way??
also what about the permission error during bootup for the ruby script?
what about the execute attribute to be on for ruby? do i need to do that? and how?

---

### Post by rubylaser on 2011-12-28
The first thing you'd want to do is chmod the script.
```
chmod +x /usr/local/bin/persistent_iscsi.rb
```

You can run the script as a test at any time by running it with ruby. No need to restart to test it out.
```
ruby /usr/local/bin/persistent_iscsi.rb
```

I should have looked at his code, the File.open line won't work as written.  It needs to be like this.
```

File.open('/root/test.tst', 'w') {|f| f.write('running') }

```

```

cat /root/test.tst

```

And to get ARGV passed it properly, it's just easier to restart.

---

### Post by TheR on 2011-12-28
> **kanu2k11 said:**
> and do i need to restart the server in order to run the script or is there another way??
also what about the permission error during bootup for the ruby script?
what about the execute attribute to be on for ruby? do i need to do that? and how?

You need to restart client machine of course. It doesn't make any logic to restart server machine in order to test client ;-)

If you have solved problem of execution permission can you please make clear which parameter is passed to ruby program. You may find out this by changing debugging line with this code:

File.open('/root/test.tst', 'w+') {|f| f.write(ARGV.first) }

and write here what is written to the file:

cat /root/test.tst


by
TheR

---

### Post by kanu2k11 on 2011-12-29
I just did a restart after doing the chmod command and adding file.open line by <rubylaser> and it is working :) 
but i tried to run the script by running 
```
ruby /usr/local/bin/persistent_iscsi.rb
```
I got the below error
```
ruby /usr/local/bin/persistent_iscsi.rb
/usr/local/bin/persistent_iscsi.rb:17: unterminated string meets end of file
/usr/local/bin/persistent_iscsi.rb:17: syntax error, unexpected tSTRING_END, expecting tSTRING_CONTENT or tREGEXP_END or tSTRING_DBEG or tSTRING_DVAR
```


Now I just want to exactly note down the steps we did to get this working so if needed I can do this for other servers..

---

### Post by kanu2k11 on 2011-12-29
Haha No No by server I meant the client which is ubuntu server. Sorry for the confusion. :)
> **TheR said:**
> You need to restart client machine of course. It doesn't make any logic to restart server machine in order to test client ;-)

by
TheR

---

### Post by rubylaser on 2011-12-29
Can you add the line that Ther suggested?  That should allow you to see what's being passed through ARGV?  Please paste that back here so we can see the format.  Also, can you please paste here what you have in /etc/iscsi/persistent.names.conf?

---

### Post by kanu2k11 on 2011-12-29
I added the line as suggested by TheR but the same error is still there when i run that script with ruby.
```
 ruby /usr/local/bin/persistent_iscsi.rb
/usr/local/bin/persistent_iscsi.rb:17: unterminated string meets end of file
/usr/local/bin/persistent_iscsi.rb:17: syntax error, unexpected tSTRING_END, expecting tSTRING_CONTENT or tREGEXP_END or tSTRING_DBEG or tSTRING_DVAR

```

/etc/iscsi/persistent.names.conf contains the following :
```
iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-static;10;iscsi/storage1
iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ede6-scripts;11;iscsi/storage2

```

---

### Post by rubylaser on 2011-12-29
What's the output of this?
```
cat /root/test.tst
```

That should so you what's being passed in ARGV.

---

### Post by kanu2k11 on 2011-12-29
the file does not exist
> cat: /root/test.tst: No such file or directory

---

### Post by kanu2k11 on 2011-12-29
this how my ruby script is
```
[RUBY]
#!/usr/bin/ruby
device = nil
File.open('/root/test.tst', 'w+') {|f| f.write(ARGV.first) }
id_lun = ARGV.first.split('-').last
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
iqn, lun, dev = line.chomp.split(';')
if lun == id_lun
device = dev
break
end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device
[/RUBY]

```

---

### Post by rubylaser on 2011-12-29
> **kanu2k11 said:**
> this how my ruby script is
```
[RUBY]
#!/usr/bin/ruby
device = nil
File.open('/root/test.tst', 'w+') {|f| f.write(ARGV.first) }
id_lun = ARGV.first.split('-').last
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
iqn, lun, dev = line.chomp.split(';')
if lun == id_lun
device = dev
break
end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device
[/RUBY]

```

Since, /root/test.tst doesn't exist, it sounds like your script is not running.  At a minimum that file should exist, and it should contain the contents of ARGV.  Can you change the File.open line slightly? The way Ther wrote it should be fine, but just try it without w+. w+ creates a new file for both reading and writing. w creates it for writing.

```
File.open('/root/test.tst', 'w') {|f| f.write(ARGV.first) }
```

---

### Post by TheR on 2011-12-29
> **kanu2k11 said:**
> this how my ruby script is
```
[RUBY]
#!/usr/bin/ruby
device = nil
File.open('/root/test.tst', 'w+') {|f| f.write(ARGV.first) }
id_lun = ARGV.first.split('-').last
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
iqn, lun, dev = line.chomp.split(';')
if lun == id_lun
device = dev
break
end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device
[/RUBY]

```

You better start to learn some programming since [RUBY] and [/RUBY] are not part of a program.

Program has 15 lines only and error is in line 17 ;-(

make debug line:
File.open('/root/test.tst', 'a') {|f| f.write(ARGV.first) }

and do:

sudo touch /root/test.tst

restart the system and see what is in /root/test.tst.


by
TheR

---

### Post by rubylaser on 2011-12-29
> **TheR said:**
> You better start to learn some programming since [RUBY] and [/RUBY] are not part of a program.

Program has 15 lines only and error is in line 17 ;-(

make debug line:
File.open('/root/test.tst', 'a') {|f| f.write(ARGV.first) }

and do:

sudo touch /root/test.tst

restart the system and see what is in /root/test.tst.


by
TheR

Jeez, I didn't even think that he was including those [RUBY] tags in his .rb file. I assumed that he didn't know how to use the Forum's [CODE] tags correctly :) [/RUBY] is on line 17... well, there's the problem if he included the Ruby tags.

---

### Post by kanu2k11 on 2011-12-30
> **TheR said:**
> You better start to learn some programming since [RUBY] and [/RUBY] are not part of a program.

Program has 15 lines only and error is in line 17 ;-(

make debug line:
File.open('/root/test.tst', 'a') {|f| f.write(ARGV.first) }

and do:

sudo touch /root/test.tst

restart the system and see what is in /root/test.tst.


by
TheR

Woops... :redface: I might have to now... Sorry.

below is what is written after a reboot in that test.tst file
```
pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:1pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0pci-0000:03:00.0-scsi-0:2:0:0pci-0000:00:1f.2-scsi-0:0:0:0pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:0ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ee6-storage1-lun-0ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ee6-storage2-lun-0
```

I get the below when i run that ruby script
```
sudo ruby /usr/local/bin/persistent_iscsi.rb
/usr/local/bin/persistent_iscsi.rb:4: private method `split' called for nil:NilClass (NoMethodError)

```

---

### Post by rubylaser on 2011-12-30
> **kanu2k11 said:**
> Woops... :redface: I might have to now... Sorry.

below is what is written after a reboot in that test.tst file
```
pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:1pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0pci-0000:03:00.0-scsi-0:2:0:0pci-0000:00:1f.2-scsi-0:0:0:0pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:0ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ee6-storage1-lun-0ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ee6-storage2-lun-0
```

I get the below when i run that ruby script
```
sudo ruby /usr/local/bin/persistent_iscsi.rb
/usr/local/bin/persistent_iscsi.rb:4: private method `split' called for nil:NilClass (NoMethodError)

```

You're getting the NilClass error method, because the script is looking for command line values populating is [ARGV ]("http://www.linuxtopia.org/online_books/programming_books/ruby_tutorial/Ruby_and_Its_World_ARGV.html")variable.  Since, you are running it by hand you are not passing it any command line opens, so it's trying to use the split method on a Nil object and failing as a result.

The directions that THeR gave you should be running this script automatically at boot (without you needing to do anything).  It is working right now, because you're getting values in the /root/test.tst file.

You should be able to verify this like he demonstrated in his [write up]("http://ubuntuforums.org/showpost.php?p=10214439&postcount=4") by running.
```
ls /dev/iscsi
```
if there are devices listed, it should be working.

---

### Post by TheR on 2011-12-30
ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ee6-storage1-lun-0
ip-172.16.1.11:3260-iscsi-iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ee6-storage2-lun-0

Yeah it works just that yours iscsi string is a bit different than mine.

Quick and dirty trick would be like this:

#!/usr/bin/ruby
device = nil
#File.open('/root/test.tst', 'o') {|f| f.write(ARGV.first) + "\n" }
exit 1 unless ARGV.first.match('iscsi')
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
iqn, lun, dev = line.chomp.split(';')
if ARGV.first.match(lun)
  device = dev
  break
end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device



/etc/iscsi/persistent.names.conf

whatever;storage1;iscsi/static
whatever;storage2;iscsi/scripts

But this is specific to your iscsi server.


When you assign new drives to server all you have to do is add specific line to persistent.names.conf and use this command:

iscsiadm -m session -R


No client machine restart is needed unless you have done something wrong ;-(


by
TheR

---

### Post by kanu2k11 on 2012-01-02
Happy New Year Guys. :)
First: I just did what you said TheR in post 50
My ruby script is exactly as you have given and yes without the [RUBY][/RUBY] :)
My persistent.names.conf looks like below:
I hope this is right as I replaced the "whatever".
```
iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-storage1;storage1;iscsi/static
iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ede6-storage2;storage2;iscsi/scripts

```
After running the iscsiadm command I got the below message:
```
 sudo iscsiadm -m session -R
Rescanning session [sid: 1, target: iqn.2001-05.com.equallogic:0-8a0906-0ae6a3c0a-7c3d255954e4ede6-storage1, portal: 172.16.1.100,3260]
Rescanning session [sid: 2, target: iqn.2001-05.com.equallogic:0-8a0906-12b6a3c0a-24cd25595514ede6-storage2, portal: 172.16.1.100,3260]
```

Also I don't have a /dev/iscsi directory
EDIT: I just checked again after a reboot to the server. The mounting is fine and I have now got a /dev/iscsi folder but it only has one link there for static and not for scripts? also the link for static is to sdd which is scripts as sde is static but I did ls in those folders and static is sde and scripts is sdd. Is something wrong?

---

### Post by TheR on 2012-01-03
> 
Also I don't have a /dev/iscsi directory
EDIT: I just checked again after a reboot to the server. The mounting is fine and I have now got a /dev/iscsi folder but it only has one link there for static and not for scripts? also the link for static is to sdd which is scripts as sde is static but I did ls in those folders and static is sde and scripts is sdd. Is something wrong?

You are on your own from here on. Learn more about technology and try to understand it. You know all the parts, just connect them together right.

Good luck
TheR

---

