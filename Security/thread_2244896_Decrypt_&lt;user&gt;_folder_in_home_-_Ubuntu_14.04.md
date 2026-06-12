---
title: "Decrypt &lt;user&gt; folder in /home - Ubuntu 14.04"
date: 2014-09-19
forum: Security
---

### Post by Danniel90 on 2014-09-19
Hello Ubuntu users, i decided to move definitely from Windows to Ubuntu this spring, but it seems my installation of Ubuntu 14.04 went wrong, i have a problem with the desktop enviroment and my screen goes black after login, and because it seems the OS and /home are installed in the same partition i can't just reinstall Ubuntu then all my data would be lost. So i tried to get back my data using another internal disk with Linux Mint 17 and booting from Live USB, but my user partition is encrypted and i dont know the way to decrypt it. 
[IMG]http://image.noelshack.com/fichiers/2014/38/1411138595-img-20140915-170340.jpg[/IMG]
[IMG]http://image.noelshack.com/fichiers/2014/38/1411062920-screenshot-09182014-05-51-04-pm.png[/IMG]
My question is, how can i get access to my user encrypted folder? There has to be a way to decrypt it by entering the username and password or something like that.

Thanks a lot in advance for any help, all that encrypted data is very important for me, i use it to study and work so i am in big trouble.

---

### Post by Danniel90 on 2014-09-19
forgot to mention that i don't have the passphrase when i installed Ubuntu 4 months ago, in other posts i've seen this passphrase is required in one step to decrypt the user folder.:(

---

### Post by Danniel90 on 2014-09-20
Somehow the Command found my passphrase file but now i have to enter the Passphrase login, but how do i get it?

(This screen shows the step in which i am right now)
[http://cdn8.howtogeek.com/wp-content/uploads/2012/06/650x200ximage143.png.pagespeed.ic.0ktRJILu6R.png](http://cdn8.howtogeek.com/wp-content/uploads/2012/06/650x200ximage143.png.pagespeed.ic.0ktRJILu6R.png)

---

### Post by bashiergui on 2014-09-20
You will need one of the following:
&#8226;the login password for the account.
&#8226;the mount passphrase used when you set up the encrypted home directory (you would have been told to write this down somewhere).


If you have either of these, you should be able to access the data by running the following command and following the prompts:```
sudo ecryptfs-recover-private /home/user
```
If you do not have either of these pieces of information, then the information is permanently lost. If there was a way to circumvent encryption, then it wouldn't be much use.

([http://askubuntu.com/questions/120206/encrypted-home-forgotten-password-but-no-passphrase](http://askubuntu.com/questions/120206/encrypted-home-forgotten-password-but-no-passphrase))

---

### Post by Danniel90 on 2014-09-26
Thanks you very much bashiergui, it woked just like you said, due my unexperience i tried other solutions but i didn't find out my passphrase until your post, so i was able to recover my data just like this:

[ATTACH=CONFIG]256725[/ATTACH]

Thank again bashiergui, your help will be somehow rewarded next week.

@Admin: Solved. You can close this thread. Thanks.

---

### Post by cariboo on 2014-09-26
@Danniel90, in stead of requesting the thread be closed, you can mark the thread solved, by going to Thread Tools at the top of the page, and selecting, Mark this thread as solved

---

### Post by sonu_SIRP on 2015-05-24
i have the password but is again asking for the mount passphrase. i dont remember it where can i find it???

you did it with just password????

you did it with just password????

---

