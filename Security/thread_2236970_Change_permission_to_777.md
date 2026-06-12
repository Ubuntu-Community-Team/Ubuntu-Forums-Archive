---
title: "Change permission to 777"
date: 2014-07-30
forum: Security
---

### Post by Fertech on 2014-07-30
Is there a way to change permission to 777 to more then  one picture. I just backup my laptop mac data but I notice I can't see some of my pictures until I change the permission to 777. I have over 14,000 pictures and I don't want waste my time changing one by one. Any ideas?

---

### Post by mooreted on 2014-07-30
Lets suppose I have a folder named "Pictures" and I want to change all the contents of that folder to "777" permissions. I would do:

chmod 777 -R Pictures

*Note the upper-case 'R'

---

### Post by Lars Noodén on 2014-07-30
777 is not right.  Maybe the file ownerships  are off?  If you run *ls -lh ~/Pictures/*, or whichever directory, do you see your account as owner and group or something else?  If you see something else, then you can change ownership back to your account using the [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1.html) utility:

```

sudo chown -R fertech ~/Pictures/
[s]chmod -R 755 ~/Pictures/[/s]

```

Edit: see thnewguy's post below, I should have re-read the line above better in the preview.  Another option would be 'chmod u=rwX,go=rX ~/Pictures/', because the uppercase X gets directories but leaves regular files alone unless they were already executable.

---

### Post by thnewguy on 2014-07-30
Changing permissions to 777 is a bad idea and not likely to be a good solution. Partly because 777 means everyone can read, write and execute the files. You should need only read permissions (or maybe write if you want to edit files. Assuming you are the owner of the directory and its files you can change all permissions on the images to 644. Try the following

```

sudo chown -R myuser ~/Pictures
find ~/Pictures -type f -exec chmod 644 {} \;
find ~/Pictures -type d -exec chmod 755 {} \;

```

The aove three lines makes you the owner of all files, then gives you read and write permission to all images (while granting read-only access to everyone else). The last line makes sure you can access all folders under the Pictures directory.

---

