---
title: "Can not upload with vsftpd"
date: 2009-08-29
forum: Server Platforms
---

### Post by markosjal on 2009-08-29
Well here goes , yet another post that will probably go un-answered or that will lead me down a road of older version problems that are not quite my same problem, but here goes. If iim really lucky i might get flamed for how stoopid I am! I have all but given up on any answers from the forums here, reallly.


I am trying to get VSFTP running . I need to configure an account for Joomla and it appears that the account can not take uploads. I am trying to upload to the /var/www which I have set as the default path for the joomla user acccount. 

I am using Ubuntu 9.04 and joomla 1.5 downloaded today. 

I think almost certainly I need some permission setting and that the OS is preventing VSFTP from writing to /var/www

Thanks in advance for any help or flames.

---

### Post by jay.parnaby on 2009-08-30
By default the /var/www directory is owned by root so it is a case of permissions.

You could try adjusting the ownership of the /var/www directory.

Change the ownership of /var/www to www-data (Apache)
```

sudo chown -R www-data:www-data /var/www

```

Enable members of the www-data group to write to the directory
```

sudo chmod -R g+w /var/wwww

```

Add your username to the www-data group
```

sudo usermod -G www-data -a your_username

```

It could be worth looking at the security implications of this before you run it though

---

### Post by markosjal on 2009-08-30
I did as youy suggested and it works . Thanks and would still appreciate any help with the Joomla/VSFTP, because I can still not get joomla to FTP on a localhost connection.

Still dead in the water.

---

