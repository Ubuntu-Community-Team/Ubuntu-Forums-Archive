---
title: "bash script = no password ?"
date: 2011-08-10
forum: Security
---

### Post by Mortuis0 on 2011-08-10
A peculiar thing happened and I was curious on how that is possible.

I'm replaying Diablo 2 these days and I decided that I would make a script so that I don't have to type the commands needed each day (.iso mount and wine with a specific parameter for the appropriate .exe). I'm using the command ```
sudo mount -o loop etc.
``` and obviously it asked for my password each time. But when I put the same command in my script and execute it, there's no password prompt, even after quitting the terminal with the su privileges.

So I made several tests (mkdir /test) in and out of the script. Finally, I do have the impression that this is a important security breach !

If I ever create a script with this command in it :

```
 sudo rm -r /* 
```

after having found the bash place (which bash), mark it executable and send it to someone I want to harm, wouldn't it work after that person had downloaded and executed the script ? Or is there something with the owner of the file ? :confused:

---

### Post by papibe on 2011-08-10
That is the common behavior, take a look at the section 'Advantages and Disadvantages' this help [page]("https://help.ubuntu.com/community/RootSudo"). It was designed as a comprise in both usability and security. In any case, the time your system remembers the password can be reduced, or set to zero if you want.

Regardless of that, I would recommend designing your scripts assuming they are run as root, and call then using sudo. Like in this [thread]("http://ubuntuforums.org/showthread.php?t=1808944&highlight=sudo+script").

Hope it helps.
Regards.

---

### Post by requeth on 2011-08-10
That is NOT a common behavior unless your commands are mucked.

I just tried typing    sudo echo worked

I was asked for a password. I did a ctrl C

I went to desktop and created a file, added the above command to it.
Saved the file.
Chmod +x 'd the file.
went back to cmd and ./ 'd the file.
I was asked for the password.

If I don't close the window then I don't need to sudo again. I closed the window and re-opened, tried executing the script again and was asked for password again.

---

### Post by papibe on 2011-08-10
> **requeth said:**
> I was asked for a password. I did a ctrl C
Try entering the password (don't press control-c), and try again.

If you don't enter the password, you don't became root, thus the password is not remembered.

Hope it clarify things a bit.
Regards.

---

### Post by Mortuis0 on 2011-08-11
Thanks Papibe for your reply ! I tried it several more times, and in fact the password got prompted while executing the script after a specific time, though I don't know how much.

I do have another issue regarding the ownership of wine : while in "sudo mode", wine don't work for it need to be executed by my user...but I guess this don't have anything to do with security discussions :p

Thanks again !
Mortuis

---

### Post by bodhi.zazen on 2011-08-11
> **Mortuis0 said:**
> I do have another issue regarding the ownership of wine : while in "sudo mode", wine don't work for it need to be executed by my user...but I guess this don't have anything to do with security discussions :p

Thanks again !
Mortuis

You should NEVER run wine as root.

[http://wiki.winehq.org/SecuringWine](http://wiki.winehq.org/SecuringWine)

---

