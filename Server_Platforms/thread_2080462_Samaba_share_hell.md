---
title: "Samaba share hell"
date: 2012-11-04
forum: Server Platforms
---

### Post by skauk on 2012-11-04
I'm a Ubuntu noob although I work in I.T. support with windows everyday. 

I have setup Ubuntu server 12.04 LTS installed samba, web in and it all runs OK thus far. However I'm using webmin to admin samba shares and I'm struggling to hell lol.

I've created a new Linux user,synced the user to samba user and passworded the account. I then sudo mkdir my folder tried it as /shared and /home/shared.

Then back to webmin create new share, called it shared browse to the folder I created owner set as the account I created (although tried leaving as root too), set the group to users and added a description.

 Next go back into share for security setting make it writable and saved.

I can use \\hub or the IP I see the shared folder and it asks me to authenticate which I do and it let's me in.......BUT I cannot write anything to the folder for love nor money why?

 All I want is to create an area that is shared for anyone who's account is in the users group and deny anyone who isn't. 

I've tried all sorts followed guide after guide deleted when failed n started again. I also restarted samba after creation too.

---

### Post by darkod on 2012-11-04
I think the linux permissions of the folder are considered different from the samba permissions. Check the permissions of /shared.

Since you want more than one user to use it, you might need to give full access to all, and then the samba permissions will limit who can write and who can't. Giving full permissions to the folder is:
sudo chmod 777 /shared

If that works and later you want to limit the permissions, you can try with 770 (the numbers are for Owner-Group-Anyone else). 7 means full read/write permissions. So, with 770 you will give the owner user full permissions, the group full permissions, and all the others no permissions.

For making user you have the owner and group as you want, you can change them with:
sudo chown username:groupname /shared

Samba is not very difficult to control using the terminal, you might wanna try that. Webmin can make it complicated and even mess it up sometimes. In one place I read that webmin is not in the repositories exactly because it's not recommended, it interacts with the filesystem in a different way and down the line you can create more issues than solve them.

---

### Post by Goodchoice on 2012-11-05
Building off the previous post, you can use ls -al to find out the permissions of the folder, here is a good example of how to read permisions [tuxfiles]("http://www.tuxfiles.org/linuxhelp/filepermissions.html").

In the webmin interfaces, if you click on the share link, there should be a security permissions link at the bottom of the page, click on that and the options that come up should include a make browsable option click on that and apply and retry to create something in the shared folder.

Goodchoice IT is a small IT company based in Surrey
[www.Goodchoiceit.co.uk](www.Goodchoiceit.co.uk)

---

