---
title: "editing files in Apache's var/www folder"
date: 2011-12-07
forum: Security
---

### Post by xtgyal on 2011-12-07
I'd like to be able to create/remove directories and add/remove/edit files in my Apache HTTP Server folder var/www using the GUI's file explorer.  The Properties tab for the folder says that the owner is root and I am not the owner so cannot change permissions.  I know I can do what I need to do via Terminal using sudo, but would really like to avoid that hassle, and be able to copy & paste and open/close the files directly in the GUI file explorer.  How do I change the permissions for that folder and would that affect my server's security?

---

### Post by Lars Noodén on 2011-12-07
If you are the only one using the web server then you can set it so that you have group ownership of the directory.

```

sudo chgrp -R xtgyal /var/www
sudo find /var/www -type d -exec chmod g=rwxs **'{}'** \;
sudo find /var/www -type **f** -exec chmod g=rws **'{}'** \;

```

If you share access to the directories with others, then use instead a group that everyone is a member of.

---

### Post by emiller12345 on 2011-12-07
I think you had a couple of typos, did you mean ...

```

sudo chgrp -R xtgyal /var/www
sudo find /var/www -type d -exec chmod g=rwxs **'{}'** \;
sudo find /var/www -type **f** -exec chmod g=rws  **'{}'** \;

```

?

---

### Post by xtgyal on 2011-12-07
It is a personal computer and I am the only user on it.  However, the web server is public, and I'm not sure whether removing the restrictions on the folder will make it vulnerable to hackers?  What exactly do those commands do?  I basically just would like to be able to use the var/www folder like I would any in the home/nicole directory (copy & paste files around, edit files, create/remove subfolders).  If I'm writing webpages, it is an incredible hassle to first save them to the /home/ directory, then use Terminal to move them to the var/www directory, I'd prefer only to deal with that if it was necessary for security.

---

### Post by josephmills on 2011-12-07
Hello there Please take a couple of min to look over 
3. Searching based on times


[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)
 

now base that on the command sed which you can learn more about here 
[http://www.youtube.com/watch?v=uutbiT2JT40](http://www.youtube.com/watch?v=uutbiT2JT40)

Hope that this helps 
Joseph

---

### Post by Lars Noodén on 2011-12-08
> **emiller12345 said:**
> I think you had a couple of typos, did you mean ...

Yes.  Thanks.

---

### Post by emiller12345 on 2011-12-08
> **Lars Noodén said:**
> Yes.  Thanks.
No prob
> **xtgyal said:**
> It is a personal computer and I am the only user  on it.  However, the web server is public, and I'm not sure whether  removing the restrictions on the folder will make it vulnerable to  hackers? 
From everything that I've heard, if your going to run a public http server, you probably want to have as few running services as possible to keep it as secure as possible. That includes running in a GUI environment. If i think I understand what Lars was getting at, by changing the group permissions of the web servers folder 'you' (echo $USER) have access to change the web files, while keeping the owner of the web pages the same.   This means that only additionally 'you' ( and probably programs executed by 'you') can make changes to the files (as well as user that could make changes before the chgrp commands)

---

### Post by dai_trying on 2011-12-19
you could just use "gksudo nautilus" and use file explorer as root.

---

### Post by xtgyal on 2011-12-30
Thanks everyone, yes "gksudo nautilus" in Terminal works great.  #Ubuntu IRC chat said that changing the user settings could be bad, and this works just as fine.

---

