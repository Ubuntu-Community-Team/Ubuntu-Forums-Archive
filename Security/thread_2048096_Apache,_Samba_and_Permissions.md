---
title: "Apache, Samba and Permissions"
date: 2012-08-26
forum: Security
---

### Post by slyme on 2012-08-26
Hello, Linux beginner here ... and loving it so far! Anyway, here's the plan:

Run Apache on Ubuntu Server for use as a development server, not exposed to the internet (yet - it's tempting) and then share the web site directory using Samba so that I can edit the files 'in place' from a variety of client machines on my local network.

So, I give ownership of the directory to the user www-data and the www-data group. This seems to work in the first instance.

I then add the appropriate user to the www-data group. Now I mount the directory on any client using the user credentials ... so far, so good ...

The problem: When I open a file with a text editor and save it then the ownership and group settings change to the logged on user:group.

This leaves some sites improperly configured ... for instance, if I edit a theme file from a Wordpress install everything works fine until I try to do the same thing through the WordpPress admin. The WordPress editor cannot save files any more.

My limited understanding suggests the following:

Change the user:group that Apache uses to the same group as the logged on user. Is this wise? I'm going to find out how to this and give it a go anyway just to see if it works but, I ask again, is this wise?

Log on remotely as www-data. I'll have to change the password for www-data so that I can use the account to log on. There is something about this idea that just ... well ... feels wrong.

Perhaps the problem is with the Samba config? Can I configure Samba so that I log on as one user:group but save files as another?

Any advice would be most welcome, thanks ... Simon.

---

### Post by SeijiSensei on 2012-08-26
You can use the "force" directives in smb.conf to tell Samba to conduct all filesystem operations with a specific Unix account regardless of the identity of the logged-in user.  

```

[website]
    path = /var/www
    force user = www-data
    force group = www-data
    {other options}


```

I use this method in office settings where multiple people might need to create web content.  If you need to make sure you know which user creates which file, this solution will not work for you.  If that doesn't matter, then using "force user/group" is a simple solution to managing permissions.

---

### Post by slyme on 2012-08-26
> **SeijiSensei said:**
> You can use the "force" directives in smb.conf to tell Samba to conduct all filesystem operations with a specific Unix account regardless of the identity of the logged-in user.  

```

[website]
    path = /var/www
    force user = www-data
    force group = www-data
    {other options}


```

I use this method in office settings where multiple people might need to create web content.  If you need to make sure you know which user creates which file, this solution will not work for you.  If that doesn't matter, then using "force user/group" is a simple solution to managing permissions.
Thank you so much SeijiSensei ... that's done the job perfectly, it's all working as hoped it would when I started this.  It's taken me two weeks to get from nothing to here ... I would have expected it to take months to figure but this forum and many others have been so very helpful, so thank you to you all.

Simon.

---

