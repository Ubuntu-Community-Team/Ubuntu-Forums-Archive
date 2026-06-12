---
title: "403 Forbidden for apache root"
date: 2009-12-22
forum: Server Platforms
---

### Post by sdlynx on 2009-12-22
I changed my default directory for apache in /etc/apache2/sites-available/default to something else (namely /windows/XAMPP/htdocs).  However, now, when I try to go to localhost, or any other folder/file in htdocs it gives me a 403 forbidden error.  I have tried sudo chmod +x /windows/XAMPP/htdocs but no dice.  Ideas?

SDLynx

---

### Post by aschlosberg on 2009-12-23
In /etc/apache2/httpd.conf you will have a bunch of directories listed with allow/deny permissions.

Add the following:

> 
<Directory /windows/XAMPP/htdocs/>
        Order Allow,Deny
        Allow from all
</Directory>This should fix the problem. If not there may be something related to the fact that you are accessing your Windows file system so check the permissions there too.

---

### Post by oneloveamaru on 2009-12-23
If you are using Ubuntu, you shouldn't have anything in /etc/apache2/httpd.conf.

Edit /etc/apache2/sites-available/default and find something like:

<Directory /windows/XAMPP/htdocs/>
Order Allow,Deny
Allow from all
</Directory> 

and either change it to look like what aschlosberg posted or just delete those lines. Both should work.

---

### Post by sdlynx on 2009-12-23
I tried both things, and they still give me a 403 error...

---

### Post by wojox on 2009-12-23
> **sdlynx said:**
> I tried both things, and they still give me a 403 error...

And you cleared the cache and restarted Apache2?

---

### Post by chenxiaolong on 2009-12-23
Can you access the files in [COLOR="SeaGreen"]/windows/XAMPP/htdocs/[/COLOR] or is it just an empty folder? If it's just an empty folder, Apache denies directory listing by default.

---

### Post by oneloveamaru on 2009-12-23
What are the actual permissions on that directory, what's inside and what does /var/log/apache2/error.log say?

---

### Post by sdlynx on 2009-12-23
> **chenxiaolong said:**
> Can you access the files in [COLOR="SeaGreen"]/windows/XAMPP/htdocs/[/COLOR] or is it just an empty folder? If it's just an empty folder, Apache denies directory listing by default.

it is a folder w/ subfolders, no content
yes, I would like it to list the folders there
either way, I've tried going to exact files and that does not work either

> **oneloveamaru said:**
> What are the actual permissions on that directory, what's inside and what does /var/log/apache2/error.log say?

[Wed Dec 23 14:47:28 2009] [error] [client ::1] (13)Permission denied: access to / denied

is the error.

actual permissions are -rwxrwx--- (I've tried changing this with sudo chmod but to not avail).

@wojox yeah

---

### Post by chenxiaolong on 2009-12-23
If you want it to list the directories you have to create a [COLOR="SeaGreen"].htaccess[/COLOR] file in [COLOR="SeaGreen"]/windows/XAMPP/htdocs/[/COLOR] containing:

```
Options +Indexes
```

Also, is the /windows folder on a NTFS partition? Linux is unable to change NTFS permissions and you will have to change them in Windows (if you have it installed).

---

### Post by sdlynx on 2009-12-23
> **chenxiaolong said:**
> If you want it to list the directories you have to create a [COLOR="SeaGreen"].htaccess[/COLOR] file in [COLOR="SeaGreen"]/windows/XAMPP/htdocs/[/COLOR] containing:

```
Options +Indexes
```

Also, is the /windows folder on a NTFS partition? Linux is unable to change NTFS permissions and you will have to change them in Windows (if you have it installed).

well that would explain that...  how do I change file permissions in Windows (I've never actually tried changing file permissions in windows).  Is it worth noting that the apache I have installed on the windows partitions works just fine?

---

### Post by chenxiaolong on 2009-12-24
On Windows, Apache runs as the user you are logged into. On Linux, Apache runs as the user "www-data." Unless your Windows user is called www-data, you won't be able to access the files, unless you change the permissions (this will only work on XP Pro/Server 200*/Vista/7):

1. Right click the folder and choose [COLOR="SeaGreen"]Properties[/COLOR].

2. Click the [COLOR="SeaGreen"]Security[/COLOR] tab.

3. Click the [COLOR="SeaGreen"]Advanced[/COLOR] button.

4. Click the [COLOR="SeaGreen"]Owner[/COLOR] tab.

5. Click [COLOR="SeaGreen"]Edit...[/COLOR]

6. Click [COLOR="SeaGreen"]Other Users or Groups...[/COLOR]

7. Type in [COLOR="SeaGreen"]Everyone[/COLOR] and click [COLOR="SeaGreen"]OK[/COLOR].

8. Check the [COLOR="SeaGreen"]Replace owner on subcontainers and objects[/COLOR] checkbox.

9. Click [COLOR="SeaGreen"]OK[/COLOR] until you get back to the properties window of your folder.

10. Now click [COLOR="SeaGreen"]Advanced[/COLOR] again (I have no idea why MS makes you exit the dialog then go in again).

11. On the [COLOR="SeaGreen"]Permissions[/COLOR] tab, click the [COLOR="SeaGreen"]Change Permissions...[/COLOR] button.

12. Deselect the [COLOR="SeaGreen"]Include inheritable permissions from the object's parent[/COLOR] checkbox (if it is checked).

13. If that checkbox was checked, click [COLOR="SeaGreen"]Remove[/COLOR] on the dialog that comes up.

14. Make sure there aren't any entries in the [COLOR="SeaGreen"]Permission Entries[/COLOR] box. If there is, remove them.

15. Click [COLOR="SeaGreen"]Add...[/COLOR] 

16. Type in [COLOR="SeaGreen"]Everyone[/COLOR].

17. Under the [COLOR="SeaGreen"]Allow[/COLOR] column, check [COLOR="SeaGreen"]Full Control[/COLOR].

16. Check the [COLOR="SeaGreen"]Re_p_lace all child object permissions with inheritable permissions from this object[/COLOR] checkbox.

17. Click [COLOR="SeaGreen"]OK[/COLOR] and Click [COLOR="SeaGreen"]Yes[/COLOR] on the dialog that comes up.

18. Click [COLOR="SeaGreen"]OK[/COLOR] twice.

That should be it...Everything in Windows is way more complicated:D

---

### Post by oneloveamaru on 2009-12-24
Your problem is this:

actual permissions are -rwxrwx--- (I've tried changing this with sudo chmod but to not avail).

It doesn't have world read or execute.

I'm not sure I would use chenxiaolong directions, he is giving Everyone permissions on that folder.

Find out the user Apache is running as, and just give it full access to the folder and then force the permissions down to all sub folders and items.

If adding Everyone is easier, just give them full access, don't make them the Owner.

---

### Post by chenxiaolong on 2009-12-24
Apache runs as www-data, which doesn't exist on Windows. You could create the user and make www-data the owner and have both www-data and your Windows user have permissions.

---

### Post by sdlynx on 2009-12-24
Unfortunately chenxiaolongs long directions did not work.  Everyone has permissions on the Windows side, and I set www-data to be the Group owner of the whole /windows partition.  And yet, still forbidden.

---

### Post by chenxiaolong on 2009-12-24
The only thing I can suggest is to try running apache as root:

[COLOR="SeaGreen"]sudo nano /etc/apache2/envvars[/COLOR]

Change [COLOR="SeaGreen"]www-data[/COLOR] to [COLOR="SeaGreen"]root[/COLOR] on the [COLOR="SeaGreen"]export[/COLOR] lines.

[COLOR="SeaGreen"]sudo /etc/init.d/apache2 restart[/COLOR]

Also, is the Windows partition mounted as read only?

---

### Post by sdlynx on 2009-12-24
when I changed the user and group to root apache fails to restart, giving this error:

```
 ... waiting Syntax error on line 145 of /etc/apache2/apache2.conf:
Error:\tApache has not been designed to serve pages while\n\trunning as root.  There are known race conditions that\n\twill allow any local user to read any file on the system.\n\tIf you still desire to serve pages as root then\n\tadd -DBIG_SECURITY_HOLE to the CFLAGS env variable\n\tand then rebuild the server.\n\tIt is strongly suggested that you instead modify the User\n\tdirective in your httpd.conf file to list a non-root\n\tuser.\n

```

I've also tried using my own username for user and group but everything is forbidden then too.

---

### Post by play_ on 2010-05-14
Did you figure this out? Having the exact same problem.

---

### Post by chenxiaolong on 2010-05-14
Windows NTFS filesystems also have permissions, which can't be set in Linux. I wonder if it will work if you create a Linux user with the same username as your Windows user and run apache as that.

---

### Post by sdlynx on 2010-05-14
> **chenxiaolong said:**
> Windows NTFS filesystems also have permissions, which can't be set in Linux. I wonder if it will work if you create a Linux user with the same username as your Windows user and run apache as that.

nah, my windows and linux usernames were the same that whole time w/ no dice.

---

### Post by Techjacker on 2010-06-15
thank you! :p

> **chenxiaolong said:**
> If you want it to list the directories you have to create a [COLOR=SeaGreen].htaccess[/COLOR] file in [COLOR=SeaGreen]/windows/XAMPP/htdocs/[/COLOR] containing:

```
Options +Indexes
```Also, is the /windows folder on a NTFS partition? Linux is unable to change NTFS permissions and you will have to change them in Windows (if you have it installed).

---

### Post by chenxiaolong on 2010-06-15
You're welcome :D!

---

