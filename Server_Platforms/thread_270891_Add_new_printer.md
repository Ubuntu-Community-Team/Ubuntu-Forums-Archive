---
title: "Add new printer"
date: 2006-10-03
forum: Server Platforms
---

### Post by st_itty on 2006-10-03
I need help with adding a new printer. I have a headless server on which I have installed cups and cups-client. I have a Epson stylus c86 connected to the server. I need to add it to the server. All the threads I saw so far talks about using the gui. I assume there is someway to do the same thing from command line. Can anyone please tell me how to add the printer from command line?
I also need to share this printer with a windows computer and a mac os x computer.
Thanks.

---

### Post by mitch.c on 2006-10-03
> **st_itty said:**
> I need help with adding a new printer. I have a headless server on which I have installed cups and cups-client. I have a Epson stylus c86 connected to the server. I need to add it to the server. All the threads I saw so far talks about using the gui. I assume there is someway to do the same thing from command line. Can anyone please tell me how to add the printer from command line?
I also need to share this printer with a windows computer and a mac os x computer.
Thanks.
This is a brief list of commands that may help you. I just don't have time to help you with a proper HOWTO

You'll need to get a proper driver (ppd) installed first. These files need to be added to /usr/share/cups/model/

You can list installed drivers (ppd) an maybe grep your model to see if it is already installed (I see a "gutenprint/5.0/en/stp-escp2-c86.5.0.ppd.gz"?):
```
lpinfo -m | grep -i c86
```
Next, get the uri (if you don't know it. This will list available device uris
```
# run with device connected and powered on
lpinfo -v
```
You can add/modify printer from the commandline like this
```
# assumes you want to use name=Stylus-C86, the ppd I listed above; you'll need to determine the deviceuri
sudo lpadmin -p Stylus-C86 -E -v <deviceuri> -p gutenprint/5.0/en/stp-escp2-c86.5.0.ppd.gz -u allow:all
```

For the Windows client, see this post: [http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)

I don't know about the Mac... someone else will help you there.

A couple of good cups references:
[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)
[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

I hope I gave you enough to go on. Good Luck.

---

