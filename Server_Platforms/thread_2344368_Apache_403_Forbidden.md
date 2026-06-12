---
title: "Apache: 403 Forbidden"
date: 2016-11-24
forum: Server Platforms
---

### Post by asearle on 2016-11-24
Hallo Everyone,

I installed Apache2 via Synaptic and it worked pretty much "out of the box": Bravo!

But now I would like to have the root directory for the server in my "Documents" directory and have created a new root directory: So far so good and, initially it worked fine and displayed the HTML-files that I had put there.

But a few days later, with the PC having been shut down a few times and Ubuntu updates being installed, I can no longer "see" the site that I created and get the message ...

"403 Forbidden
You don't have permission to access /name.php on this server."

I googled a lot and, following recommendations, changed the chmod of the directories but this all seems to be wrong as the site will still not display ... and it did display originally.

There seems to be a lot of suggestions out there about this but so far nothing I have found has fixed it.

Maybe someone out there can point me towards a good HOWTO?

Many thanks,
Alan
Cologne

---

### Post by slickymaster on 2016-11-24
*Thread moved to **Server Platforms**.*

---

### Post by cariboo on 2016-11-24
Have you got mod_userdir enabled? If not, run the following command:

```
sudo a2enmod userdir
```

Then make sure the permissions of the directory are set to 755 eg:

```
chmod -R 755 ~/public_html
```

change the ~/public_html to the directory you are using.

You didn't say what version you are running, but to reload apache2 after you have made the changes:

```
sudo service apache2 reload
```

or for 16.04 or later use:

```
systemctl reload apache2.service
```

---

### Post by asearle on 2016-11-27
Many, many thanks for this tip. I tried this and researched other posts giving instructions on the settings of permissions and feel that I learnt a lot but ...

Arrrggghhh!

It turned out to be MY SYNTAX: I had made a small change to a directory name in the path to the new location and so, of course, it didn't work. The "403 Forbidden" message was really telling me that the directory I wanted to reference didn't exist.

So the main lesson learnt here is that you should always double-check that the directory/path information is 100% correct.

How embarrassing. I do apologise.

Many thanks (anyway).

Yours,
Alan

---

