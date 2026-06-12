---
title: "Cant view my website"
date: 2018-01-12
forum: Server Platforms
---

### Post by mpell94 on 2018-01-12
Hello!

I created a new 16.04 Ubuntu server, installed apache2 and put my website files inside of /var/www/html. When I go to a web browser and type in my IP address, I get this message...

[IMG]https://i.stack.imgur.com/gjPTA.png[/IMG]

I have ufw enabled, I allowed apache, port 80 is open, I have set 777 permissions for /var/www/html (for testing purposes) and it simply just wont display my index.html

Anyone have any suggestions?

Cheers!

---

### Post by QIII on 2018-01-12
Hello.

Don't ever use 777 on anything publicly exposed.  Not even for testing.  I don't even do that on my development machine at home.  Avoid getting into bad habits.

It's also best to use IPTables directly rather than ufw.

You may be getting that error due to improper permissions/ownership.  Set the permissions  appropriately, set the owner of the directories and files appropriately.  See what happens then.

At that point, troubleshooting can be done under the appropriate conditions.

Cheers!

---

### Post by mpell94 on 2018-01-12
Its not public yet, we are testing it internally and I know I was just frustrated so I set it to 777, but I'll try not to do it in the future....

I ended up figuring it out though

somehow nginx was installed on my server but when I went to do a apt-get remove nginx it said it was not installed....

so I did a ps -elf | grep nginx and sure enough it was there...

Next I did a kill -9 of that process and restarted apache2 and checked the site and it worked!!

Then i went into the opt folder and found the only thing in the opt folder was the directory of nginx, and did a rm -R * of that and now its working beautifully

Thanks :)

---

### Post by QIII on 2018-01-12
Woot!

If you would, please mark the thread solved so that it will be easier for others to find later.

---

