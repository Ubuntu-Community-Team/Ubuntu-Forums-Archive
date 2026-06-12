---
title: "Ubuntu server"
date: 2016-01-09
forum: Server Platforms
---

### Post by lance13 on 2016-01-09
Hello!
Unfortunately I'm completely new to ubuntu, but my website is running on it and theres no other option for me, I connect over a SSH client.
So when everything was set up for me, I saw the ubuntu apache2 document page as index.html, however when I try to change the index.html in /var/ww/ it does not let me..

Any support would be highly appreciated!

Thanks

[http://prntscr.com/9nwi1d](http://prntscr.com/9nwi1d) for example

---

### Post by Magnus_Forsblom on 2016-01-09
Try typing sudo su to ssh and then type your root user password.
Then you should be able to change the index.html file.

---

### Post by howefield on 2016-01-09
Thread moved to the "*Server Platforms*" forum.

Probably better to post your terminal output here (between code tags) rather than send people off to view an image.

---

### Post by lance13 on 2016-01-09
I did that, but still don't have permission...
Im trying to change the index.html over SFTP..

---

### Post by The Cog on 2016-01-09
That is probably not possible. I think you will need to use ssh to gain command-line access. Then you can do it two ways. 

1: 
Copy the file to your home directory where it can be copied/replaced with SFTP, then copy it back to the correct location. e.g. log in using SSH and run these commands to make a copy of the index that you can edit with SFTP and then replace the contents of the real file:
```
touch index.html
sudo cp /var/www/index.html .
```
Now you can edit or replace this local copy using SFTP. Then copy the contents back into the proper location.
```

sudo cp index.html /var/www/

```

For an explanation of sudo read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
The initial touch command creates a file which you have permission to edit, so the copy command doesn't then create a file owned by root that you can't edit.

2:
Just edit the file using a command-line editor. This is OK if the edits are small or if (unlikely) you feel at home with a linux command-line editor. nano is a simple editor that you should be able to use. Use ctrl-X to exit and it will ask if you want to save the changes
```
sudo nano /var/www/index.html
```

---

### Post by mastablasta on 2016-01-09
download index.html change it in preferred editor (bluefish will do well, but notepad++ or sublime text are also good), fix it and then upload it. to connect via sftp i suggest Filezilla. works well.

also i suggest into looking for various tools for an easier website creation (wordpress, joomla, drupal...).

---

