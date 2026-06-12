---
title: "How do I turn off parental controls?"
date: 2006-11-19
forum: Ubuntu Christian Edition
---

### Post by HareBall on 2006-11-19
I was trying to get to my home page and got a message telling me there is a banned phrase found. The page is Google.com and I have it set to run my personal page which includes my gmail account. I don't mind having some things blocked, but this is a bit much. It's not a porn site or chat room or anything.:confused:

It's working now. I don't know what the difference is, but it wasn't allowing it through and then I went back and now it is.

Ok, it is doing it again. This is pretty annoying. How do I get rid of Dansguardian?

---

### Post by ReaderRat on 2006-11-19
Please see my post:
**[http://www.ubuntuforums.org/showthread.php?t=300583](http://www.ubuntuforums.org/showthread.php?t=300583)**
There is a solution listed, but when I did it, I lost the Internet - had to set up everything again....cure is worse than the disease.

EDIT:  I did want to upgrade to Edgy, so it was no big loss. Don't want you to go through this though....ReaderRat

---

### Post by HareBall on 2006-11-19
> **ReaderRat said:**
> Please see my post:
**[http://www.ubuntuforums.org/showthread.php?t=300583](http://www.ubuntuforums.org/showthread.php?t=300583)**
There is a solution listed, but when I did it, I lost the Internet - had to set up everything again....cure is worse than the disease.

EDIT:  I did want to upgrade to Edgy, so it was no big loss. Don't want you to go through this though....ReaderRat

I went ahead and tried it. I have the same problem you had with Firefox. I tried uninstalling it and reloading. Didn't work](*,) 
I can get to the internet using Opera, but I want my Firefox back.
I posted a question in the beginner forums to see what I might be able to find out before I do a reinstall.

---

### Post by mhancoc7 on 2006-11-19
> **HareBall said:**
> I went ahead and tried it. I have the same problem you had with Firefox. I tried uninstalling it and reloading. Didn't work](*,) 
I can get to the internet using Opera, but I want my Firefox back.
I posted a question in the beginner forums to see what I might be able to find out before I do a reinstall.


Sorry that you are having trouble. One easy fix would have been to simply add google.com to the "Sites Not Filtered" using the Configure Parental Controls GUI.

To completely remove dansguardian you should do the following.

```
apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
```

You will also need to unlock the firefox proxy settings using the script attached. Simply extract the file and then double click on the "unlock_proxy" file and choose run in terminal.

You can also unlock the proxy settings using the Configure Parentals Controls GUI. I am working on ways to make this easy, but the main goal was to have pre-configured parental controls. I don't want to make it to easy to bypass them. :)

God Bless, Jereme

---

### Post by HareBall on 2006-11-19
> **mhancoc7 said:**
> Sorry that you are having trouble. One easy fix would have been to simply add google.com to the "Sites Not Filtered" using the Configure Parental Controls GUI.

To completely remove dansguardian you should do the following.

```
apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
```

You will also need to unlock the firefox proxy settings using the script attached. Simply extract the file and then double click on the "unlock_proxy" file and choose run in terminal.

You can also unlock the proxy settings using the Configure Parentals Controls GUI. I am working on ways to make this easy, but the main goal was to have pre-configured parental controls. I don't want to make it to easy to bypass them. :)

God Bless, Jereme

I did this, now Firefox gives me a message saying: Firefox is configured to use a proxy server that is refusing connections.
I am having to use Opera to p[ost and surf the internet.
The reason I wanted to remove dansguardian is that we don't have any children, so there is noone to block web content from. I agree that it should be there for houses with children and should be very hard to get around. I wish I had known how to allow Google before I uninstalled it.](*,)

---

### Post by mhancoc7 on 2006-11-19
> **HareBall said:**
> I did this, now Firefox gives me a message saying: Firefox is configured to use a proxy server that is refusing connections.
I am having to use Opera to p[ost and surf the internet.
The reason I wanted to remove dansguardian is that we don't have any children, so there is noone to block web content from. I agree that it should be there for houses with children and should be very hard to get around. I wish I had known how to allow Google before I uninstalled it.](*,)

Hmmm:-k

Well, you could use the [dansguardian script ]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html")to re-install the filtering and then use the Configure Parental Controls GUI to allow google.com.

Jereme

---

### Post by HareBall on 2006-11-19
> **mhancoc7 said:**
> Hmmm:-k

Well, you could use the [dansguardian script ]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html")to re-install the filtering and then use the Configure Parental Controls GUI to allow google.com.

Jereme
I reinstalled Dansguardian and I am about to reboot and see where I am.

OK, I am able to use Firefox again and got it to open Google.com. How do I add websites to it that I want access to?

---

### Post by mhancoc7 on 2006-11-20
> **HareBall said:**
> I reinstalled Dansguardian and I am about to reboot and see where I am.

OK, I am able to use Firefox again and got it to open Google.com. How do I add websites to it that I want access to?

Great!

You can use the "Configure Parental Contols" GUI. (System>Administration>Configure Parental Controls)

This will open a simple GUI frontend that allows you to edit the dansguardian configuration files. It allows gives you access to the Access Denied Log and other things.

Let me know if you have any trouble.

God Bless, Jereme

---

### Post by HareBall on 2006-11-20
> **mhancoc7 said:**
> Great!

You can use the "Configure Parental Contols" GUI. (System>Administration>Configure Parental Controls)

This will open a simple GUI frontend that allows you to edit the dansguardian configuration files. It allows gives you access to the Access Denied Log and other things.

Let me know if you have any trouble.

God Bless, Jereme

Working great, thanx. It helps when you know what you are doing:rolleyes:

---

### Post by liberiauser on 2006-11-20
Question from newbie:

I installed Ubuntu CE on a friend's system and Firefox not connecting.

I get a system proxy dialog, I am on another computer and do not remember what it said exactly.

I do not have the "Configure Parental Contols" GUI. (System>Administration>Configure Parental Controls)

dansguardian does not seem to be installed. (from advanced install)  I tried to run it and got errors.

any suggestions to get the parental controls off completely? 
run the script? supplied in a previous post?

Where did the Configure Parental controls go? I'll use them if I can get this loaded up

this is a new installation of the latest Ubuntu, with CE added to it. 

Thanks

---

### Post by mhancoc7 on 2006-11-20
> **liberiauser said:**
> Question from newbie:

I installed Ubuntu CE on a friend's system and Firefox not connecting.

I get a system proxy dialog, I am on another computer and do not remember what it said exactly.

I do not have the "Configure Parental Contols" GUI. (System>Administration>Configure Parental Controls)

dansguardian does not seem to be installed. (from advanced install)  I tried to run it and got errors.

any suggestions to get the parental controls off completely? 
run the script? supplied in a previous post?

Where did the Configure Parental controls go? I'll use them if I can get this loaded up

this is a new installation of the latest Ubuntu, with CE added to it. 

Thanks

So did you use the convert_me script? If so did you use it on Dapper or Edgy? The current scripts are only designed for Dapper. I am working on the Edgy versions now.
God Bless, Jereme

---

### Post by doobit on 2006-12-02
> **mhancoc7 said:**
> So did you use the convert_me script? If so did you use it on Dapper or Edgy? The current scripts are only designed for Dapper. I am working on the Edgy versions now.
God Bless, Jereme

I used the Edgy convert me script. Almost everything is working fine, but the GUI parental controls don't do anything when I click on them (except the link to the site). I tried downloading the configuration script, but it's blocked because it's a .gz
Where is are the control scripts located? Can I edit them in the terminal? I'm not afraid of a CLI.

---

### Post by Darrious on 2006-12-02
I would first just try to reinstall it that would be your best bet for trying to get it to work again. 
 
I really would not know why the GUI is not working it should be absoloutly fine.
 
Also, I've had problems, not with this specific topic, but with gnomesword. It has been giving me trouble. It does not allow me to install any other programs and I don't know why. It has something to do with the program itself I suppose. Maybe the Ubuntu CE conversion script will get a little bit more advanced and allow you to choose whether or not to install gnomesword.

---

### Post by mhancoc7 on 2006-12-02
> **doobit said:**
> I used the Edgy convert me script. Almost everything is working fine, but the GUI parental controls don't do anything when I click on them (except the link to the site). I tried downloading the configuration script, but it's blocked because it's a .gz
Where is are the control scripts located? Can I edit them in the terminal? I'm not afraid of a CLI.

I would suggest running the convert_me script again. I am not sure why, but sometimes the dansguardian setup doesn't install all the confi files correctly. The users who have had this issue simply ran the script again and it was fixed.

The dansguardian conf files are located in the /etc/dansguardian directory. I would suggest the script once more before editing them by hand.

Jereme

---

### Post by chach man on 2007-06-03
I deleted dansguardian out of package manager and now firefox cant find the proxy server.

I tried to reinstall it through the package manager with no secsess. if I re delete it by using the code posted before:

              apt-get --purge remove --assume-yes "dansguardian"
              apt-get --purge remove --assume-yes "tinyproxy"
              apt-get --purge remove --assume-yes "clamav"
              apt-get --purge remove --assume-yes "firehol"
              apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"

will this continue to be a problem or
how can i find the information to get back onto te web or
as a last resort how can I reinstall the dreaded dansguardian so that firefox will work again

---

### Post by mhancoc7 on 2007-06-03
> **chach man said:**
> I deleted dansguardian out of package manager and now firefox cant find the proxy server.

I tried to reinstall it through the package manager with no secsess. if I re delete it by using the code posted before:

              apt-get --purge remove --assume-yes "dansguardian"
              apt-get --purge remove --assume-yes "tinyproxy"
              apt-get --purge remove --assume-yes "clamav"
              apt-get --purge remove --assume-yes "firehol"
              apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"

will this continue to be a problem or
how can i find the information to get back onto te web or
as a last resort how can I reinstall the dreaded dansguardian so that firefox will work again

I would suggest that you reinstall dansguardian with the script available here ([www.mirror.christianubuntu.com](www.mirror.christianubuntu.com)). Once installed you should open the dansguardian gui and Unlock Firefox Proxy settings. Then you can use the code you mentioned to remove it all. Now you can adjust the Firefox proxy settings and should be able to access the web.

Jereme

---

