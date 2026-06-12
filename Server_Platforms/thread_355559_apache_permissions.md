---
title: "apache permissions"
date: 2007-02-07
forum: Server Platforms
---

### Post by Compact on 2007-02-07
Which are the best permissions to set to files and folders that are inside the apache public folder and have to be accessible by remote users? And the owner?

---

### Post by kidders on 2007-02-07
Hi there,

It's always good practice to grant the minimum possible access to resources on your system. In your case, as long as apache can traverse your directory tree and read the contents of files, that should be enough.

A usual practice might be the result of something like this:
```
sudo chmod -R 644 /var/www/wherever
sudo chmod -R +X !$
```

The effect would be something like the following:[LIST]
[*]File owners get read/write access.
[*]Directory owners get read/write/traverse access.
[*]The whole world gets read access to files.
[*]The whole world gets read/traverse access to directories (although, I imagine read permission is not always necessary).
[/LIST]

In octal terms, files would be 644, and directories would be 755 or maybe 751.

If any of your scripts require looser access restrictions (eg the ability to write debug logs or list directory contents), the settings I've described will break them though.

---

### Post by Compact on 2007-02-07
Thanks! The owner and group of the files should be www-data?

---

### Post by kidders on 2007-02-07
No, not necessarily. Many would consider that a security risk, since (in theory) a bug or security issue in apache could result in the modification of local files. You could make root the owner ... or maybe even yourself, if you find that convenient.

In _my_ www directories...[LIST]
[*]root owns most files/directories.
[*]www-data and other users own one or two things, where appropriate.
[*]A small group of www editors has the group ownership of most stuff.
[/LIST]

Basically though, you can do almost anything you want. The important thing is to understand the effect your choice of settings will have. Beyond that, it's just a question of good practice ... unless of course what you're running is security sensitive.

I hope that helps.

---

### Post by mafsi on 2007-12-06
> **kidders said:**
> Hi there,

It's always good practice to grant the minimum possible access to resources on your system. In your case, as long as apache can traverse your directory tree and read the contents of files, that should be enough.

A usual practice might be the result of something like this:
```
sudo chmod -R 644 /var/www/wherever
sudo chmod -R +X !$
```

The effect would be something like the following:[LIST]
[*]File owners get read/write access.
[*]Directory owners get read/write/traverse access.
[*]The whole world gets read access to files.
[*]The whole world gets read/traverse access to directories (although, I imagine read permission is not always necessary).
[/LIST]

In octal terms, files would be 644, and directories would be 755 or maybe 751.

If any of your scripts require looser access restrictions (eg the ability to write debug logs or list directory contents), the settings I've described will break them though.

Hi, i know this is an old post but it seems it fits to my needs.
i create a folder public_html in my /home/user & edited the sites-available/defaul to point to /home/mafsi/public_html

i installed a Joomla CMS and i have a problem: all components (i.e files that i upload via my CMS) get www-data group & owner

```
sudo chmod -R 755 /home/mafsi/public_html
&
sudo chmod -R +X !$
```

will be correct for me?

Thanks in advanced!

---

### Post by kidders on 2007-12-06
> **mafsi said:**
> i know this is an old postHehe.

> **mafsi said:**
> all components (i.e files that i upload via my CMS) get www-data group & ownerShort of "chmod -R 777 *" that's about as insecure as you can get. For files uploaded by apache, you don't have much choice though.

Something in the ballpark of "chmod 644" will work for these files, although (since www-data owns them all) "chmod 600" (or even 400) is all that's strictly required.

Having said all that, most people (including me!) would say that the permissions assigned to files owned by the user a web server is running as are essentially irrelevant in most cases, since such files are very often exposed to the whole world anyway.

I hope that helps.

---

### Post by mafsi on 2007-12-06
> **kidders said:**
> Hehe.

Short of "chmod -R 777 *" that's about as insecure as you can get. For files uploaded by apache, you don't have much choice though.

Something in the ballpark of "chmod 644" will work for these files, although (since www-data owns them all) "chmod 600" (or even 400) is all that's strictly required.

Having said all that, most people (including me!) would say that the permissions assigned to files owned by the user a web server is running as are essentially irrelevant in most cases, since such files are very often exposed to the whole world anyway.

I hope that helps.

i think u didn't get my idea :popcorn:

my files are 644 & dirs are 755 that's ok for me as long as the files have these permissions. my problem is that apache assign www-data as owner of files & i can't operate correctly my CMS. I can operate perfectly if files are 644 and dirs 755 only if i'm the owner. Since the owner is www-data i have errors operating the website.

Ideea behind this is how to tell apache that everything i upload via CMS belongs to user: mafsi not to www-date;

right now  all files that i upload to extend functionality to the site i have to go inside CMS and apply :

```
chown -R mafsi:mafsi /dir_problem
```

10x a lot

---

### Post by kidders on 2007-12-07
> **mafsi said:**
> i think u didn't get my ideaSorry. The o/p was as follows, so I made certain assumptions hehe...
> **Compact said:**
> Which are the best permissions to set to files and folders that are inside the apache public folder

> **mafsi said:**
> Ideea behind this is how to tell apache that everything i upload via CMS belongs to user: mafsi not to www-dateUnless you've done something odd with your system configuration, that can't be done. The www-data user can't create files it doesn't own, and even if it could, it wouldn't necessarily be able to write to them, which is a necessary part of performing an upload.

Why do you need to chown uploaded files?

---

### Post by mafsi on 2007-12-07
my friend Joomla is a CMS (Content Management System) and to extend it's functionality i install some modules, components, plugins (like PHPNuke, if you know); 

Ok, the component is installed but with owner www-data which makes imposibble that componet to run proper.:idea:

---

### Post by kidders on 2007-12-07
I don't know PHPNuke I'm afraid, but if you have to do something non-standard with access control to make it work, I'd have thought they would tell you how. :-(

Who is PHPNuke supposed to run as?

---

### Post by mafsi on 2007-12-14
> **kidders said:**
> I don't know PHPNuke I'm afraid, but if you have to do something non-standard with access control to make it work, I'd have thought they would tell you how. :-(

Who is PHPNuke supposed to run as?

ok solved the problem Kidders.

in 
```

/etc/apache2/apache2.conf
```

there is a section where www-data was set as default as user & group 4 apache www; i changed it with my username & group

---

### Post by kidders on 2007-12-14
> **mafsi said:**
> there is a section where www-data was set as default as user & group 4 apache www; i changed it with my username & group

Hey again,

If what you mean is that apache now runs as you, be very careful ... that's an *exceptionally* unwise configuration. Apache should _never_ run as a user that can log in, has a shell, owns anything except the minimum possible number of files, or would have any reason to exist if you uninstalled your web server.

If your web server is never bound to externally accessible network interfaces, the issue is less critical, but in all other cases, I would very strongly recommend restoring apache's original user account settings.

---

### Post by mafsi on 2007-12-15
Thanks for advise, but my server is  not for productions outside. is just to create websites & to show to my clients & afterthat they will me boved to a secure server.

---

