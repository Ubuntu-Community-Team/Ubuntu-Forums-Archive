---
title: "script to automatic delete exe file in ubuntu"
date: 2009-03-04
forum: Server Platforms
---

### Post by ssffzzxx on 2009-03-04
Dear All, 
I have an ubuntu that share a folder using samba on LAN.
Windows xp client, using a folder from ubuntu samban server.

I need a script in my ubuntu server to automatic delete exe file in the shared folder (\home\share folder).

Your help will be apprecited.
Thanks and Regards

---

### Post by HermanAB on 2009-03-04
A simple cron job will do, but why would you want to do that?

---

### Post by ssffzzxx on 2009-03-04
Hi Herman, 
Thanks for your prompt help :)
I need this because, I have XP client that using map folder form ubuntu, and Sometimes user put games installer in the shared folder, or sometime there is also a virus, with exe extension.

I want to make sure that my users never copy an installer using USB disk to the network.

Let my check the link that you gave to me.
Thanks again.

Cheers

---

### Post by ssffzzxx on 2009-03-04
Hi Herman, 
I still can't figure it out how to delete it, because i can't find on the link that you gave to me.


Thanks

---

### Post by HermanAB on 2009-03-05
Make a little script called delexe like this:

#! /bin/bash
rm /wherever/*exe

Make it executable:
# chmod 754 delexe

Put it in /etc/cron.hourly
# mv delexe /etc/cron.hourly

Cheers,

Herman

---

### Post by ssffzzxx on 2009-03-05
Hi Herman, 
Thanks a lot, I will put this script to my ubuntu.


Best Regards

---

### Post by ssffzzxx on 2009-03-05
Hi Herman, 
If I read the script, I am not sure that it can delete exe file in the sub folder, because I have many folder with lots of sub in it.

This script will delete only exe file in the parent folder.. CMIIW
Thanks Herman, it seems i have to learn scripting for automat many process..

Regards

---

### Post by bluefrog on 2009-03-05
find /where -name *.exe -exec rm "{}" ;\

---

### Post by ssffzzxx on 2009-03-05
Hi bluefrog, 
Many thanks for the script, let me try first, to create this script as a cron job.

many thanks also for you Herman.
This forum help me so much.

Thanks and Regards

---

### Post by ssffzzxx on 2009-03-05
Dear BlueFrog, 
I got this error:
find: missing argument to `-exec'

is there something missing ?
Thanks and Regards

---

