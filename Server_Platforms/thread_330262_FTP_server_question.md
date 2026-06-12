---
title: "FTP server question"
date: 2007-01-02
forum: Server Platforms
---

### Post by Coogan on 2007-01-02
Here's my setup.  I've got ProFTP running on my Dapper system.  When you log into it, you're dropped into /home/ftp which has separate upload and download subdirs.  This works just fine for just general uploading and downloading.  However, I'd like to use Dreamweaver's publishing feature to upload my webpages, which are in /www/[domain]/.  My question is, how can I set up ProFTP to put me in /home/ftp or /www based on which username I use when I log in?

I thought that setting up a virtual host would fix it, but it didn't work, and when I looked up the documentation on virtual hosts, it indicated that unlike Apache, each virtual host must be tied to a distinct separate IP address.  Is that correct?

---

### Post by chrisfay on 2007-01-03
The folder restrictions can get much more detailed than just locking users into their home directories. You can lock everyone into their home folder, but then allow a certain group to access another. Here's and excerpt from Proftpd's site:

> #
# A more complex setup where all users are locked into 
# their home except those in group 'staff' who are 
# locked into /u2/allweb
#
<VirtualHost myhost.mynet.foo>
DefaultRoot ~ !staff
DefaultRoot /u2/allweb staff
</VirtualHost>

As you can see, the default root says anyone except group staff is stuck in home. In your case, create a new group and put your user in it. Lock that group's folder into /var/www or whatever you need to access and give only that group access to it. The rest will be stuck in home.

Here's more info from their site:

[http://www.proftpd.org/localsite/Userguide/linked/chroot.html](http://www.proftpd.org/localsite/Userguide/linked/chroot.html)

---

### Post by Coogan on 2007-01-03
Ahh, I wasn't aware you could have multiple DefaultRoot directives.  Must've missed that part in the docs.

Thanks for the tip.

---

### Post by Coogan on 2007-01-03
One last clarification: it looks like using your method, having multiple user accounts to use for ftp is mandatory.  Just having one isn't going to work, because that one will be in group X, which will either have or not have access to a specified DefaultRoot.  If you want one group to have a DefaultRoot of /www/[domain] and another to have a DefaultRoot of /home/ftp, then you have to have 2 users as well.  I'd imagine that if you added the ftp user to both groups, it'd default to whatever DefaultRoot it encountered first or last, but not both.  Correct?

---

### Post by chrisfay on 2007-01-03
You would need to create a specific group for the second defaultroot location. With the group being the defining factor, you would obviously want only users who should be locked into /var/www/domain to be included. There's no point in having a user that should be locked into his home folder also be listed in your new group that's locked into /var/www/domain. That would completely defeat the purpose. 

> Just having one isn't going to work, because that one will be in group X, which will either have or not have access to a specified DefaultRoot.

I'm not sure I follow here. Your question is based around multiple users correct? By this:
> My question is, how can I set up ProFTP to put me in /home/ftp or /www based on which username I use when I log in?

....i assumed that you had multiple users on your system.

If you don't have multiple users than it would be a non issue apart from security precautions surrounding the one user. 

You would need at least two for this to be relevant. One that's locked into the home directory and a second, in a completely second group, thats given separate access.

---

