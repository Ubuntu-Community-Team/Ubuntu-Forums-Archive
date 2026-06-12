---
title: "question about permissions and the apache2 public folder"
date: 2015-03-12
forum: Server Platforms
---

### Post by Drone4four on 2015-03-12
Would it be a good idea to swap the apache2 public_html folder into the home directory of a regular user ?  Or would it be safer and a better idea to keep it in the default location /var/www/DN/public_html in which changes can only be made as root user?  (Keep in mind that I am running 14.04 on a remote DigitalOcean droplet, which is why I have a root user.) If it's safer to keep the public_html folder in /var/www/DN/ modifiable only by root, then would it be unwise to change chmod permissions to 0777 for the apache2 public folder?  What about changing permissions to 0664 or 0644?

---

### Post by nerdtron on 2015-03-13
> Or would it be safer and a better idea to keep it in the default  location /var/www/DN/public_html in which changes can only be made as  root user?
From my standpoint I don't see any significant advantage to move the html folder to other folders, unless the new folder will be on a faster/bigger partition. And you will have to deal with apparmor if you move the folder.

> If it's safer to keep the public_html folder in /var/www/DN/ modifiable  only by root, then would it be unwise to change chmod permissions to  0777 for the apache2 public folder?  What about changing permissions to  0664 or 0644? 

You definitely don't want 0777 on any folder/file in a linux filesystem. The default for directories 755 and for file 644 is a good choice. An important thing to keep in mind is that for websites/web folders, all files should be world-readable, meaning 640 or 750 (last bit 0) permission is not advisable.

---

### Post by TheFu on 2015-03-14
Just change the owner and permissions in the /var/www/ area to whatever you like. But .... be very careful, since this can make hacking your box next to trivial.  It is smart to have that area read-only for the apache process owner (or whatever web server you run) and only allow apache write to specific directories, as required, under that area.  Remember, the core to Unix security is file and directory permissions. Master those first.

The ~/public_html/ areas for users are part of a module to allow every end user with their own website.  When implemented, they are accessed like [http://domain.com/~userid/](http://domain.com/~userid/) - nice and you don't have to set these up for individual userids.  So - I wouldn't.

---

### Post by Drone4four on 2015-03-14
Sorry, guys, I should have included in my original post my reasoning on why I asked the question that I did.

> **nerdtron said:**
> From my standpoint I don't see any significant advantage to move the html folder to other folders ...   

The advantage that I see in re-locating my public folder to a regular user is that it would be safer.  I figure frequently updating my HTML and content via ssh as root user every day would be foolish.  I assumed it'd be safer to ssh into a regular user and make all my changes that way.  

Referring to the public folder, **TheFu**, writes: > It is smart to have that area read-only for the apache process owner (or whatever web server you run) and only allow apache write to specific directories, as required, under that area.  Remember, the core to Unix security is file and directory permissions. Master those first.

So are you two saying that it'd be better security practices to make all my HTML changes locally and then mirror my local file-tree to my remote file-tree in /var/www/ as root user via rsync once a week?

---

### Post by TheFu on 2015-03-15
> So are you two saying that it'd be better security practices to make all my HTML changes locally and then mirror my local file-tree to my remote file-tree in /var/www/ as root user via rsync once a week? 

When did I say that?   NO!

I said the different locations have a different purpose and that using one location for the wrong purpose is a bad idea. I suggested that you use normal file and directory permissions to make editing files in /var/www easy, while maintaining security for the web server process and allowing the web server read-only access to the files.

---

### Post by Drone4four on 2015-06-29
> **TheFu said:**
>  When did I say that? NO!
I said the different locations have a different purpose and that using one location for the wrong purpose is a bad idea. I suggested that you use normal file and directory permissions to make editing files in /var/www easy, while maintaining security for the web server process and allowing the web server read-only access to the files.


You deserve an enormous apology, **TheFu**.  In the process of summarizing your advice, I butchered it.  I was way off.  Please disregard my folly.  

Back to the discussion.  

So you people are saying that it's a bad idea to set permissions to 0777 recursively from a top level directory.  Preserving tight read only permissions is important in the interests of a secure web server.  

I notice that when I upload a snapshot of a web page project I've been playing with on to my DigitalOcean droplet into my /var/www/public/[remotehost]/public_folder as root, when I visit the page in my browser, the images are inaccessible.   ls -l in my img/gallery directory prints the permissions of every file.  Here is an example of a single file from this directory in particular: ```
-rw-r----- 1 root root  806308 Jun  1 23:30 1.jpg
``` The images render with ```
# chmod -R 0755 *
``` but I gather that changing permissions like this is insecure with all files and folders set to 0755.  With 0755 the permissions for this same image reads: ```
-rwxr-xr-x 1 root root  806308 Jun  1 23:30 1.jpg
``` That gives web surfers more access than is necessary.  Given the advice of the forum members so far, it's safer to make these files readable but not writeable, nor executable. As per this thread, I invoke ```
# chmod -R 0644 *
``` inside my img directory and the images render fine.  This changes the permissions label via ls -l to: ```
 -rw-r--r-- 1 root root  806308 Jun  1 23:30 1.jpg
```. So my image folder is secure and renders as it should (behaves properly).  

Changing the permissions of specific files and directories, especially for my testcase, is simple and straight forward.  But its gonna be real tedious to do so for each and every file and directory on my entire website.  Is there a faster way to set all folders from a top level directory to 0755 and and set all files to 0644?  I can't do chmod -R 0755 * because that changes all files AND folders to 0755.  If I do chmod -R 0644 *, then the images don't render.  The only way to get them back is to chmod the folders with 0755.  Again this is not a complicated procedure, but it's tedious to do so for every file and folder in a gigantic website with dozens of sub directories, each with unique img folders.   How could I use chmod at a top level folder to invoke proper permissions for a giant directory tree?  Would writing a bash script be my next step?  Are there any other options to automate permissions security for a larger website?

---

### Post by bab1 on 2015-06-30
> **Drone4four said:**
> ...

So you people are saying that it's a bad idea to set permissions to 0777 recursively from a top level directory.  Preserving tight read only permissions is important in the interests of a secure web server. 
The permissions 0777 on files and directories allow all users to have read, write and execute permissions.  What possible reason would anyone have to allow  everyone to have the ability to create code and execute that code from anywhere in that branch of the file system.  If your goal is to allow all users access to a specific directory then all you need is read and execute permissions for the directories along the entire file system path.  This can be 555 or 755 or 775.  The trailing number denotes all the users on the system (others).  This means that all users only need read and execute permissions to traverse the directory path to the file and the ability to read the file.  > 

I notice that when I upload a snapshot of a web page project I've been playing with on to my DigitalOcean droplet into my /var/www/public/[remotehost]/public_folder as root, when I visit the page in my browser, the images are inaccessible.   ls -l in my img/gallery directory prints the permissions of every file.  Here is an example of a single file from this directory in particular: ```
-rw-r----- 1 root root  806308 Jun  1 23:30 1.jpg
``` The images render with ```
# chmod -R 0755 *
``` but I gather that changing permissions like this is insecure with all files and folders set to 0755.  With 0755 the permissions for this same image reads: ```
-rwxr-xr-x 1 root root  806308 Jun  1 23:30 1.jpg
```

All new data is created with the permissions set by umask.  A directory is created with 777 permissions and set with the umask.  On Ubuntu the default umaks is 0002 for mortal users (non-system and not root).  The root user umask is 0022.  These allow for directory creation of 0775 for mortal users and 0755 for the root user.  Files are set with the same umask.  They are created with 0666 and set with the umask to 0664 for users and 0644 for root.  I see that your setting is 0640.  What is the umask of the droplet?  Or did you set the permissions before you uploaded the files?   

Changing the permissions of specific files and directories, especially for my testcase, is simple and straight forward.  But its gonna be real tedious to do so for each and every file and directory on my entire website.  Is there a faster way to set all folders from a top level directory to 0755 and and set all files to 0644?  I can't do chmod -R 0755 * because that changes all files AND folders to 0755.  If I do chmod -R 0644 *, then the images don't render.  The only way to get them back is to chmod the folders with 0755.  Again this is not a complicated procedure, but it's tedious to do so for every file and folder in a gigantic website with dozens of sub directories, each with unique img folders.   How could I use chmod at a top level folder to invoke proper permissions for a giant directory tree?  Would writing a bash script be my next step?  Are there any other options to automate permissions security for a larger website?

You shouldn't have to reset the permissions if you set the ownership and permissions correctly.  Unfortunately the convenient ownership and permissions may not be the most secure settings.  Security is always a trade off  between security and convenience.

FYI you can set the permissions with symbolic notation and avoid setting all the files executable.  It is far easier, however, to setup the ownership and permissions on an empty directory and then add the data.  If you copy data it should retain the original permissions.  It you move the data (mv) you should get the same permissions you will get on newly created data.

---

### Post by Drone4four on 2015-07-04
Thanks for the reply, **bab1**.  

> **bab1 said:**
> FYI you can set the permissions with symbolic notation and avoid setting all the files executable.  It is far easier, however, to setup the ownership and permissions on an empty directory and then add the data.  If you copy data it should retain the original permissions.  It you move the data (mv) you should get the same permissions you will get on newly created data.
I could back up my old public folder, create a new public folder, set file permissions to 644 and directory permissions to 755, then move the old public folder contents to the new one.  This might not be exactly what you were suggesting, but that&#8217;s what I was thinking of trying until I came across the official Ubuntu community help page for [FilePermissions]("https://help.ubuntu.com/community/FilePermissions") which addresses this issue specifically.  Here is the relevant piece of advice:
> **Recursive Permission Changes**
To change the permissions of multiple files and directories with one command. Please note the warning in the chmod with sudo section and the Warning with Recursive chmod section.

**Recursive chmod with -R and sudo**

To change all the permissions of each file and folder under a specified directory at once, use sudo chmod with -R

```
user@host:/home/user$ sudo chmod 777 -R /path/to/someDirectory
user@host:/home/user$ ls -l
total 3
-rwxrwxrwx  1 user user 0 Nov 19 20:13 file1
drwxrwxrwx  2 user user 4096 Nov 19 20:13 folder
-rwxrwxrwx  1 user user 0 Nov 19 20:13 file2
Recursive chmod using find, pipemill, and sudo
```

To assign reasonably secure permissions to files and folders/directories, it's common to give files a permission of 644, and directories a 755 permission, since chmod -R assigns to both. Use sudo, the find command, and a pipemill to chmod as in the following examples.

To change permission of only files under a specified directory.

```
user@host:/home/user$ sudo find /path/to/someDirectory -type f -print0 | xargs -0 sudo chmod 644
user@host:/home/user$ ls -l
total 3
-rw-r--r--  1 user user 0 Nov 19 20:13 file1
drwxrwxrwx  2 user user 4096 Nov 19 20:13 folder
-rw-r--r--  1 user user 0 Nov 19 20:13 file2
```
To change permission of only directories under a specified directory (including that directory):

```
user@host:/home/user$ sudo find /path/to/someDirectory -type d -print0 | xargs -0 sudo chmod 755 
user@host:/home/user$ ls -l
total 3
-rw-r--r--  1 user user 0 Nov 19 20:13 file1
drwxr-xr-x  2 user user 4096 Nov 19 20:13 folder
-rw-r--r--  1 user user 0 Nov 19 20:13 file2
```

This document is a little daunting.  There is a lot of information here.  I will play around with the suggested commands.

---

### Post by bab1 on 2015-07-05
> **Drone4four said:**
> Thanks for the reply, **bab1**.  


I could back up my old public folder, create a new public folder, set file permissions to 644 and directory permissions to 755, then move the old public folder contents to the new one.  This might not be exactly what you were suggesting, but that’s what I was thinking of trying until I came across the official Ubuntu community help page for [FilePermissions]("https://help.ubuntu.com/community/FilePermissions") which addresses this issue specifically.  Here is the relevant piece of advice:


This document is a little daunting.  There is a lot of information here.  I will play around with the suggested commands.
Essentially when you use *find * and pipe it to the chmod command you are using chmod on only files.  You can do the same with the directories.  But why do that.  When a user other than root create the directories they have the default permissions of 775 and when you create files they will have the permissions of 664.  If you do this as root the permissions are 755 and 644.

So whether you chmod all all the extant directories or create new files and directories the results should be the same.  There is always ore than one way to get to the end result.

Now what to you do if there are multiple users with access to the file system?  Each user will have ownership for themselves normally.  In this situation, If john creates a directory or file the ownership is john:john.  If Bill creates a a directory of file the the owneship is bill:bill.  The point is that permissions are only part of the equation.  Ownership is important too.

---

### Post by Drone4four on 2015-07-23
> Essentially when you use*find*and pipe it to the chmod command you are using chmod on only files. You can do the same with the directories. But why do that?  

My problem is that root configured the apache public folder in /var/ which was initially owned by the root user.  So I have to navigate to /var/www/domanname/public_folder and recursively reset the permissions of files and directories to allow the regular user to read and write.

> When a user other than root create the directories they have the default permissions of 775 and when you create files they will have the permissions of 664. If you do this as root the permissions are 755 and 644.
...
Now what do you do if there are multiple users with access to the file system? Each user will have ownership for themselves normally. In this situation, If john creates a directory or file the ownership is john:john. If Bill creates a a directory of file the the owneship is bill:bill. The point is that permissions are only part of the equation. Ownership is important too.

If I want to change ownership to a regular user, should I be looking into chown?

As root user I executed these commands in my top level public_html directory in /var/www/:

```

# find * -type d -print0 | xargs -0 chmod 0755
# find * -type f -print0 | xargs -0 chmod 0644
# exit

```

After executing those commands, the contents of a subsequent folder has permissions which remain as follows:

```

drwxr-xr-x 2 root root    4096 Mar  8 20:55 img
-rw-r--r-- 1 root root   16956 Mar  8 20:55 index.html

```

What am I doing wrong?

---

### Post by TheFu on 2015-07-23
Steps:

Make a new group.

Put all the users you want to be able to write into that group.  I would just edit the /etc/group file.

Change the group recursively in the directory area you want.  chgrp -R

Set the "**setgid**" permission bit on all the directories, recursively.  chmod g+s

Make all the userids involved (in the group) have a umask of 002 - cannot hurt to make this the system default on Ubuntu systems going forward.

In the end, you won't need to use root ever again to manage files in this area.

Play around with this stuff in a temporary area under /tmp - make a new top level directory and play around with 4-10 other userids - see what works and what doesn't. The permissions are extremely flexible and subtle AND elegant, once understood.

---

### Post by Drone4four on 2015-07-24
Thank-you TheFu for ur reply. I won't have access to my Desktop and droplet until late next week.  I will use your 5 step guide and report back here then.

---

### Post by Drone4four on 2015-07-30
Here are TheFu's steps again.  I've added numbers:

> 
1.Make a new group.
2. Put all the users you want to be able to write into that group. I would just edit the /etc/group file.
3. Change the group recursively in the directory area you want. chgrp -R
4. Set the "setgid" permission bit on all the directories, recursively. chmod g+s
5. Make all the userids involved (in the group) have a umask of 002 - cannot hurt to make this the system default on Ubuntu systems going forward.

Tonight I looked into #3.  I changed the user group from root to my primary ordinary user.  This is the command I settled with, executed in my top level apcphe web directory: ```
sudo chgrp -R [$user] public_html/
``` Here is a sample ls- la output from any given sub directory now:```
drwxr-xr-x 5 root [$user]    4096 Mar  8 20:55 ..
-rw-r--r-- 1 root [$user]   44093 Mar  8 20:55 003 (1).gif
```
Tomorrow I will look into #1+#2

---

### Post by CharlesA on 2015-07-30
Looks like you changed the group that was assigned successfully. Good luck with #1 and #2. :)

---

### Post by Drone4four on 2015-08-02
I carefully reiviewed two docs called "[https://help.ubuntu.com/community/FilePermissions"]FilePermissions](")" courtesy of the official Ubuntu docs and, "[Linux Users and Groups]("https://www.linode.com/docs/tools-reference/linux-users-and-groups")" courtesy of Linode

First I edited the /etc/group file to include my regular user as having permission to use sftpcloudfs.  For the hell of it, I gave my user access to bin, ssh, ssl-cert and mysql.  The line with sudo already included the regular user.

For shnicks I entered: ```
sudo find /path/to/someDirectory -type f -print0 | xargs -0 sudo chmod 644
``` and ```
sudo find /path/to/someDirectory -type d -print0 | xargs -0 sudo chmod 755 
``` this time as regular user with sudo (which is distinct from last time when I entered those commands as root user w/o sudo).

However the simple, million dollar command which enabled my regular user to write to the /var/www/DNS/public_html folder was, 'sudo chown [$user] -R *' via sftp with my ftp client.

Here are **CharlesA**'s suggestions point by point again:
> 1.Make a new group.
2. Put all the users you want to be able to write into that group. I would just edit the /etc/group file.
I didn't make a new group but I did add my regular user to the group in /etc/group.

> 3. Change the group recursively in the directory area you want. chgrp -R
This was accomplished previously.

> 4. Set the "setgid" permission bit on all the directories, recursively. chmod g+s
I gather that setting the umask can be done two ways. The first with chmod is with syntax which looks like this: 'chmod u+r,g+x <filename>.'  The second method is using octal format.  I opted for the octal format.  I used the prescribed find command. Here it is again: ```
sudo find /path/to/someDirectory -type f -print0 | xargs -0 sudo chmod 644
```My question for you guys now, is: Is that sufficient? Am I missing something here having used the elaborate 'find' command instead of setgid?

> 5. Make all the userids involved (in the group) have a umask of 002 - cannot hurt to make this the system default on Ubuntu systems going forward.

Again, I'm a little bit lost here. The unmask I used for directories was 755 and for files I used 644.  When and why would it be desirable to have files and directories set to 002? Like for restricting permissions for a given user to only be writable only?

---

### Post by bab1 on 2015-08-02
> **Drone4four said:**
> 
I gather that setting the umask can be done two ways. The first with chmod is with syntax which looks like this: 'chmod u+r,g+x <filename>.'  The second method is using octal format.  I opted for the octal format.  I used the prescribed find command. Here it is again: ```
sudo find /path/to/someDirectory -type f -print0 | xargs -0 sudo chmod 644
```My question for you guys now, is: Is that sufficient? Am I missing something here having used the elaborate 'find' command instead of setgid?
You missed a lot! You had been advised to create a separate group and add users to that group if you wanted to **share data**.  What you have done is not a good method to allow access to executables.  The tool chmod (**CH**ange **MOD**e) has nothing to do with umask or the setgid (SGID) bit.  The umask is set globally in a couple of places and can be set per user in the .bashrc.  Umask sets the default file permissions on all directories and files **created** by the user.
> 

Again, I'm a little bit lost here. The unmask I used for directories was 755 and for files I used 644. 

Here is an example of where you have misunderstood.  The umask is a **filter** used to set the created directory and file permissions.  All directories are created with the permissions of 777 and the umask sets the default permissions.  If you have a umask of 002 and that is subtracted from the 777 permissions you get the default permissions of 775.  Files are created with 666 permissions and the umask of 002 subtracted provides the default file permissions of 664.  None of this sets the SGID bit.
> 
When and why would it be desirable to have files and directories set to 002? Like for restricting permissions for a given user to only be writable only?
You question here is misplaced.  You need to understand two distinct areas of access control.  Users and Groups (including SGID) and file and directory permissions along with what umask does.

---

### Post by TheFu on 2015-08-03
sudo shouldn't be needed after the ownership is changed to the userid you control.
umask doesn't mean what you've got there.  

The chmod -R g+s is not optional. It is mandatory for this to work.

I didn't read everything else carefully - looked awfully complicated for what is needed.

You don't need sudo nearly as often as you are using it.

File and directory permissions are something you either understand or you do not.  Please spend the time to learn them now.  Actually work through a tutorial and run the commands in a test directory on your own system. There isn't any other way to learn this stuff that I know.  You have to do it or you will never get this correct.

It is 'umask' - unmask is incorrect.

---

### Post by Drone4four on 2015-08-10
I did miss a lot.  Thanks guys for grounding me and thanks for your continued patience.  

Adding users, creating groups, adding users to groups, along with changing permissions and ownerships are simple procedures on Linux. For practice I created a number of dummie users, dummie groups and played around a bit in the CLI.  That was fun.  Once I learned what I set out to do, in my production environment, I created a group with 'sudo groupadd web-dev' . I added my user to the group with, 'sudo adduser $username web-dev' . Then I changed the group ownership of my public_html directory with 'sudo chgrp -R web-dev public_html.  The user ownership remains $username from earlier.  So 'ls -l' now prints:
```

user@host:/var/www/html/DNS $  ls -l
total 60
-rw-r--r--  1 $user root    25615 Mar  8 06:49 access.log
-rw-r--r--  1 $user root       13 Jul  3 22:29 c5038170a381.html
-rw-r--r--  1 $user root    11510 Mar  6 14:22 index.html
drwxr-xr-x  2 $user root     4096 Mar  8 06:49 logs
drwxr-xr-x 23 $user web-dev  4096 Aug  7 00:35 public_html
drwxr-xr-x  3 $user root     4096 Jul 30 21:47 test
----------------------------------------------------------------------------------------------------------------------------- 22:50:30
user@host:/var/www/html/DNS $ 

```
That crosses up and squares away nicely the first 3 of 5 suggestions from **TheFu**.  Am I right? Can someone verify whether or not I completed the first 3 steps adequately?

My success this time with usernames and groups is thanks to the Google search (I Googled 'groups and permissions in linux') which turned up some great guides.  The 4th result from the top as of this writing is a YouTube video posted by &#8220;Eli the Computer Guy.&#8221; The video title is, &#8220;[Users, Groups and Permissions in Linux]("https://www.youtube.com/watch?v=zRw0SKaXSfI")&#8220; .  One YouTuber in the comments section regards this video as &#8220;probably the most useful video on the entire internet.&#8221; I agree.  

The first result for that same query on Google turns up a guide courtesy of Linode, titled, &#8220;[Linux Users and Groups]("https://www.linode.com/docs/tools-reference/linux-users-and-groups")&#8221; .  I actaully viewed this guide first.  It seemed like Chinese to me.  But after having so much fun with Eli's tutorial, this Linode guide then magickally turned into easily understandable and practical English.   Thank-you Eli!  What remains on my plate to learn is TheFu's #4 + #5 (chmod g+s).  The Linode guide touches on chmod g+s but it doesn't go into enough detail. I found a doc titled, &#8220;[Using SGID to Control Group Ownership of Directories]("http://www.library.yale.edu/wsg/docs/permissions/sgid.htm")". At first glance it's pretty confusing.  But I haven't really sat down to read it thoroughly.  I'll be back next time tackling #4 and #5.

---

### Post by CharlesA on 2015-08-12
I haven't really used the sticky bit much at all, so I can't really help you there.

The user and group permissions look ok to me.

---

### Post by bab1 on 2015-08-12
> **CharlesA said:**
> I haven't really used the sticky bit much at all, so I can't really help you there.

So there is no confusion on this point, we don't need the *sticky bit *at all in this case.  The **sgid bit** (setgid) is what we are talking about here.

---

### Post by CharlesA on 2015-08-12
> **bab1 said:**
> So there is no confusion on this point, we don't need the *sticky bit *at all in this case.  The **sgid bit** (setgid) is what we are talking about here.

Thanks for the clarification. I must have been thinking of the right thing with the wrong name. :)

---

### Post by Drone4four on 2015-08-17
The purpose of using the **setgid** command is to preserve the group permissions when an authorized group member moves or copies new files/folders into a subsequent directory. In my last post I successfully changed the permissions and group ownership of my public_html folder.   Today I entered 'sudo chmod g+s public_html'  (actually I did this in /var/www/ - - above DNS/public_html).  Therefore future changes made by web-dev group users will now inherit the properties I established previously. I accomplished this task thanks to insight from the Wikipedia entry on file permissions relevant specifically to setgid:

>  The*set group ID,*setgid, or SGID permission. When a file with*setgid*is executed, the resulting process will assume the*group ID*given to the group class. When setgid is applied to a directory, new files and directories created under that directory will inherit their group from that directory. (Default behaviour is to use the primary group of the effective user when setting the group of new files and directories, except on BSD-derived systems which behave as though the setgid bit is always set on all directories (See*Setuid).)

In my test file tree on my local machine I copied a file from outside the experimental directory to inside the experimental directory.   ls -l prints the copied file as belonging to the original group.  I issue 'sudo chmod g+s path/to/directory' .  Now when I add new files, the group ownership is retained.  So I can definitively cross out #4 of #5 .  

In that same experimental directory, I noticed that the permissions for recently copied files or folders don't match the umask of their new siblings.  I presume this is where setting the umask to 002 properly is what I have to play with next.  In my test directory, folders have umasks of *drwxrwxr-x*.  Files have umasks of *-rw-r-----*.That's set correctly.  But when I drag and drop a file using my file manager into the experimental directory, the umask for the newly created file reads: *-rw-rw-r--*.  And I don't want to have to manually set the permissions every time I add a file.  So in order to preserve the desired permissions, that's where #5 comes in.  **TheFu** wrote: 

> #5 Make all the userids involved (in the group) have a umask of 002 - cannot hurt to make this the system default on Ubuntu systems going forward. 

With the remark about default settings on Ubuntu, he's not suggesting for me to go to my root directory and cast, 'sudo chmod -R 002 /'  That would be stupid.  So what was **TheFu** really getting at?

---

### Post by bab1 on 2015-08-18
> **Drone4four said:**
> In [an] experimental directory, I noticed that the permissions for recently copied files or folders don't match the umask of their new siblings.  I presume this is where setting the umask to 002 properly is what I have to play with next.  

In my test directory, folders have umasks of *drwxrwxr-x*.  Files have umasks of *-rw-r-----*.That's set correctly.  But when I drag and drop a file using my file manager into the experimental directory, the umask for the newly created file reads: *-rw-rw-r--*.  And I don't want to have to manually set the permissions every time I add a file.
With the remark about default settings on Ubuntu, he's not suggesting for me to go to my root directory and cast, 'sudo chmod -R 002 /'  That would be stupid.  So what was **TheFu** really getting at?
The umask is not set with chmod.  File permissions per se are not set umask.  The term umask means "user mask of file creation permissions" in other words the umask is a filter used to set the file (or directory) permissions when the file is created.  So umask has to do with file permissions but it is NOT in itself file permissions.  The tool chmod is use to change the mode (permissions) on a file by a user.

Here is an experiment that should enlighten you.  In your home directory as that user (not root) create a directory```
mkdir xumask

```
Now make that directory the current working directory```
cd xumask
```
Check to make sure you are in that directory```
pwd
```
Now check the umask```
umask
```It should be ```
002
```All files are created have 666 permissions initially and the umask is subtracted from that.  The current umask of 002 should yield a file with the permissions of 664.  See if that is so.  Create a test file with this command```
touch test
```Check the permissions with this```
ls -l
``` you should have a file with permissions like this```
-rw-rw-r-- 1 bab bab 0 Aug 17 23:04 test
```

Now lets change the umask setting like this```
umask 077
```Then create some more files like this```
touch test1 test2 test3
```What do you have for permissions now?  As you can see, the umask sets the permissions on newly created files.  How would you change the permissions?  With chmod like this```
chmod 664 tes*
```Noiw create another new file```
touch last-one
```What are the permissions on all the files?  How do you set the file creation permissions to what you want?

Umask is used to set the file permissions you want on all files created, while chmod is to change permissions you find that are not correct..

---

### Post by TheFu on 2015-08-18
> **Drone4four said:**
> 
With the remark about default settings on Ubuntu, he's not suggesting for me to go to my root directory and cast, 'sudo chmod -R 002 /'  That would be stupid.  So what was **TheFu** really getting at?

File permissions and umask are related, but not directly.

**umask** only controls the possible default permissions at file creation time. It is a mask, just ilke a netmask is a mask for which IPs are on the same subnet.  An xor is performed to determine the permissions for the new file. You should not use a umask in any command directly, unless it specifically takes a umask parameter. Definitely don't use it for chmod. That would be bad.

**chmod** controls the possible permissions AFTER a file is already created.

Oh - and since we know almost everything on a Unix machine is really just a file (sure - some things are "processes"), directories get the same treatment.  Once you understand file and directly permissions ... system security becomes easier.  Managing who can access devices becomes easier ... they are just files after all.

To see how umask works ... play in a test area for about 5 minutes. Change the umask to a few different values and create some empty files using "touch file1" between each umask change.  Try 022, 002, 700, 070, 750, 057, ... pretty soon you will recognize some patterns that jump out.

Ah ... I see that bab1 has already replied ... we are in different timezones and I'm a morning person. ;) His explanations are usually better than mine.

---

### Post by Drone4four on 2015-08-21
Thank-you **bab1** and **TheFu** for your detailed replies.  I'd like to especially thank you, **bab1**, for the time and care you put into your CLI suggestions.  

Some time ago, **bab1** commented on the reasoning why umask is set to 002: 

>  Here is an example of where you have misunderstood. The umask is a*filter*used to set the created directory and file permissions. All directories are created with the permissions of 777 and the umask sets the default permissions. If you have a umask of 002 and that is subtracted from the 777 permissions you get the default permissions of 775. Files are created with 666 permissions and the umask of 002 subtracted provides the default file permissions of 664. None of this sets the SGID bit. 

I had fun playing around with umask and chmod in my experimental directory of dummie files.  By setting a umask of 002, all the files created afterwards have permissions as follows: *-rw-rw-r--* which I noted corresponds to changing the mode of a given file with a 664 parameter.  I also noticed that directories are now conceived with the permission setting *drwxrwxr-x*, as if I had just changed the mode to 775.  Is that what I am trying to achieve?   

I read somewhere else that files could be set to 664 or 644 and directories could be set to 755 or 775.  So for the umask I can use 022 or 002.  022 gives the group read but not write while 002 only gives the group read access.  Keeping in mind that for my purposes, these will be the permissions for managing php, html, images, css and javascript files and directories.

---

### Post by bab1 on 2015-08-21
> **Drone4four said:**
> Thank-you **bab1** and **TheFu** for your detailed replies.  I'd like to especially thank you, **bab1**, for the time and care you put into your CLI suggestions.  

Some time ago, **bab1** commented on the reasoning why umask is set to 002: 



I had fun playing around with umask and chmod in my experimental directory of dummie files.  By setting a umask of 002, all the files created afterwards have permissions as follows: *-rw-rw-r--* which I noted corresponds to changing the mode of a given file with a 664 parameter.  I also noticed that directories are now conceived with the permission setting *drwxrwxr-x*, as if I had just changed the mode to 775.  Is that what I am trying to achieve? 
> 
Since all files are created with 666 permissions before umask is applied, then 002 will provide 664 permissions for files and 775 for directories.  What you are trying to achieve is not an absolute black or white decision.  The decision should be based on what you are trying to do with the section of the file system you are working with.  

If you want a group of  users to act upon a common file system (directories and subdirectories) while restricting all other users you must use a umask of 002.  The whole idea is to manage the group owners permission and not be concerned with the creator (owner) ownership or permissions.  The trick to doing this is using the setgid bit (SGID) for group ownership inheritance. 
 
I read somewhere else that files could be set to 664 or 644 and directories could be set to 755 or 775.  So for the umask I can use 022 or 002.  022 gives the group read but not write while 002 only gives the group read access.  Keeping in mind that for my purposes, these will be the permissions for managing php, html, images, css and javascript files and directories.
How are you managing the sites?  What application(s) are you using?  Wordpress, Joomla, Drupal?  What users are in the group you created (www-dev)?

Is the Apache user in the www-dev group?  If the Apache user has write permissions and that user is compromised all your web sites will be defaced and the databases hacked.  I understand that Wordpress, Joomla and Drupal use this form of insecure ownership/permissions for the maintainers convenience. 

I would not add the Apache user (www-data) to the www-dev group.  I would never allow write permission to the Apache user (www-data).  Other users can have write permissions via the www-dev group.  At this point I can't give you a meaningful answer until I can really see what you are doing.

Personally I set things up in the most secure way I can and only lessen the security when I understand the risks and I'm willing to take that risk.  For example, Joomla can be configured for web tools with the user www-data in the user group of the DocumantRoot (insecure) or using SSH and SFTP and without the user www-data in that group (secure but inconvenient).  I choose the latter.

---

### Post by Drone4four on 2015-08-27
> **bab1 said:**
> How are you managing the sites?  What application(s) are you using?  Wordpress, Joomla, Drupal? Nah, I’m not using Wordpress, Joomla or Drupal.  I’ve adapted a Twitter Bootstrap theme based on a template provided by a helpful Udemy course. I’ve adapted the style sheets.  In terms of content, I’ve got essays and prose on controversial topics marked up in HTML which I intend on concealing from the public Google index. More in this thread [here]("http://ubuntuforums.org/showthread.php?t=2214166"). 

> I would not add the Apache user (www-data) to the www-dev group.  I would never allow write permission to the Apache user (www-data). Other users can have write permissions via the www-dev group.    So you would recommend that I set up separate users and groups? One user and group for running Apache (without write access) and another user grouped separately for adding the HTML, CSS  and Javascript to the Apache public folder (with write access)? Is that what you are suggesting, **bab1**?  The user who adds content can be a member of www-dev group, with read, write, execute permissions, but should only require everyone else to be read only.  So that means 0774.  Right?  The www-dev group members will be adding the content requires read, write + execute while Others just need read access.  There is no need for Others to execute anything.  Therefore 0774 seems most appropriate.  The owner of the Apache2 process doesn't need to be a member of the group responsible for making changes to directories below DocumentRoot (/var/www/DN/public_html).  Is that correct? (That isn't a rhetorical question.) Can you verify whether or not I am on track or off track here?

> At this point I can't give you a meaningful answer until I can really see what you are doing. My next pet project is to set up Open Web Analytics so I can track and capture metadata of page viewers, like IP address and ISP locations of site visitors.  There is some great documentation on OWA required permissions [here]("http://wiki.openwebanalytics.com/index.php?title=Required_permissions").  That’ll be fun setting up. I'll create a new thread if I encounter questions.  

Security is important to me and I am thankful for your insight, **bab1**.

Thanks for your attention and for your patience.

---

### Post by bab1 on 2015-08-28
> **Drone4four said:**
> ... 
So you would recommend that I set up separate users and groups? One user and group for running Apache (without write access) and another user grouped separately for adding the HTML, CSS  and Javascript to the Apache public folder (with write access)?  Is that what you are suggesting, **bab1**?  

Not exactly.  What I said was the the user that is the owner of the apache2 process (i.e the apache user) should only have read access to the DocumentRoot area.  By default that is /var/www/html/<site> which is configured by the /apache/sites-available/<site-name>.conf file to direct the web server to the DocumentRoot of your choice.  It is this part of the file system (the Doc Root) the should not be writeable by the user that is running the apache.  The Apache user in Ubuntu 14.04 is the user www-data.  You can see that here ```
 ps -ef|grep apache
root      1146     1  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1147  1146  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1148  1146  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start

```
The root user starts Apache.  Then the process ownership is dropped to the www-data user.
> 
The user who adds content can be a member of www-dev group, with read, write, execute permissions, but should only require everyone else to be read only.  So that means 0774.  Right?  

0774 on what?  As I see it the DocRoot directory is owned by root:web-dev and the permissions are 0775 if you are the only mortal user (human) that is going to add working with the files.  If there is to be multiple users then the permissions should be 2775 on the DocRoot directory.  Whom ever is going to have read/write access to the DocRoot and sub-directories should be in the www-dev group.  
> 
The www-dev group members will be adding the content requires read, write + execute while Others just need read access.  There is no need for Others to execute anything.  Therefore 0774 seems most appropriate.  The owner of the Apache2 process doesn't need to be a member of the group responsible for making changes to directories below DocumentRoot (/var/www/DN/public_html).  Is that correct? (That isn't a rhetorical question.) Can you verify whether or not I am on track or off track here?

Close but no cigar!  Why the permissions of 0774?  How did you come to that conclusion after all that has been posted here before?

How does the Apache user have read access the files files in the DocRoot?  The Apache user has access via the others user group, as you have said.  The group *others* needs read and **[SIZE=3]traversal[/SIZE]** rights to the DocRoot directory.  That is the trailing **[COLOR="#FF0000"]5[/COLOR]** as in 077**[COLOR="#FF0000"]5[/COLOR]**.  The executable bit set on the directory allows those users to decend into and past that directory.  So if the user needs access to the subdirectory of some directory then that user (owner, group, others) needs the executable bit to be set on that directory.

It is worth noting hre that if you have multiple sites, the each one will have a separate DocRoot and should have a separate user group that is administering the content of that site.  I use www-content as my user group, but if I had multiple sites I would use something like www-<site> as the user group (where <site> is the various site names). 
> 

My next pet project is to set up Open Web Analytics so I can track and capture metadata of page viewers, like IP address and ISP locations of site visitors.  There is some great documentation on OWA required permissions [here]("http://wiki.openwebanalytics.com/index.php?title=Required_permissions").  That’ll be fun setting up. I'll create a new thread if I encounter questions.  

Security is important to me and I am thankful for your insight, **bab1**.

Thanks for your attention and for your patience.
The ownership and permissions are best set to allow the Apache user (www-data) read access via the others group (i,e. world readable).  The group ownership permissions can provide read/write access to multiple users via an assigned group if needed (and you must set the sgid bit).  The user ownership and permissions are only needed if there is no user group other than the users private gorup (UPG) (e.g user:user).

File system security is more a matter if seeing the scenario and applying the needed ownership and permissions.  I start with ownership and then look at the permissions.  Most of the time I do this in my head, but it might help for you to draw it out on paper or create a document with the information.  At the very least you might create a separate section of the file system to try all of this out.  I think @TheFu has mentioned this earlier.

---

### Post by Drone4four on 2015-08-28
> **bab1 said:**
> Not exactly.  What I said was the the user that is the owner of the apache2 process (i.e the apache user) should only have read access to the DocumentRoot area.  By default that is /var/www/html/<site> which is configured by the /apache/sites-available/<site-name>.conf file to direct the web server to the DocumentRoot of your choice.  It is this part of the file system (the Doc Root) the should not be writable by the user that is running the apache.  The Apache user in Ubuntu 14.04 is the user www-data.  You can see that here ```
 ps -ef|grep apache
root      1146     1  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1147  1146  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1148  1146  0 20:58 ?        00:00:00 /usr/sbin/apache2 -k start

```
The root user starts Apache.  Then the process ownership is dropped to the www-data user.


That last comment is key.  Root starts Apache and designated regular users then take over adding content.  This way if an attacker compromises the content creator user, the attacker will be prevented from compromising the root user who owns Apache.  I got it.  

> Close but no cigar!  Why the permissions of 0774?  How did you come to that conclusion after all that has been posted here before?

How does the Apache user have read access the files files in the DocRoot?  The Apache user has access via the others user group, as you have said.  The group *others* needs read and **[SIZE=3]traversal[/SIZE]** rights to the DocRoot directory.  That is the trailing **[COLOR="#FF0000"]5[/COLOR]** as in 077**[COLOR="#FF0000"]5[/COLOR]**.  The executable bit set on the directory allows those users to decend into and past that directory.  So if the user needs access to the subdirectory of some directory then that user (owner, group, others) needs the executable bit to be set on that directory. 

I could have been more clear. The reason why I suggested 0774 was b/c I didn't see why it was necessary for world to have execute permissions.  But now that you've point it out, I understand that world needs execute permissions to **traverse** directories.  OK so 0775 it is.

> It is worth noting here that if you have multiple sites, the each one will have a separate DocRoot and should have a separate user group that is administering the content of that site.  I use www-content as my user group, but if I had multiple sites I would use something like www-<site> as the user group (where <site> is the various site names). 

I don't have vhosts set up, but I was thinking of working on that eventually too. I'll be sure to have a unique user adding content for each website.  Thanks for the info.

---

### Post by bab1 on 2015-08-28
> **Drone4four said:**
> That last comment is key.  Root starts Apache and designated regular users then take over adding content.  This way if an attacker compromises the content creator user, the attacker will be prevented from compromising the root user who owns Apache.  I got it.  


Still not exactly correct.  The root user starts Apache because only root can bind with TCP/IP ports below 1024 ((i.e port 80).  Then the process forks and the user www-data runs Apache (serves the web pages).  This user does not need to be able to write the pages it serves only read them.  It is more likely that the attacker will compromise the Apache user and therefore deface the web site it the Apache user has write permissions to the DocumentRoot.  Some PHP based management tools suggest that the Apache user be allowed write permissions via a user group.  NOT A GOOD IDEA.

The mortal user (you in this case) should have read and write permissions to the files (664) and **[SIZE=3]r[/SIZE]**ead**[SIZE=3][/SIZE]** and **[SIZE=3]w[/SIZE]**rite and e**[SIZE=3]X[/SIZE]**ecute permissions (rwx = 7) on the directories of the Doc Root.  The **_Apache user (www-data) has NO write permissions_** to any directories or files in the DocumentRoot.  The Apache user is a member of the *user gorup others* as is every user.  When the permissions are set to world read able then the Apache user can read the file.  By default this is how Ubuntu is set up.  The default permissions (775 directories and 664 files will work.  Just do not add the user www-data to the group that manages the DocumentRoot content (e.g www-dev or some such). 

Apache being started by root and then forking the process to www-data is a separate concept from managing the content of the web server (the DocumentRoot).  The tow arenot related other than we are talking about how user permissions affect security.

---

