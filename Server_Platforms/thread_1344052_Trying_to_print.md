---
title: "Trying to print"
date: 2009-12-02
forum: Server Platforms
---

### Post by zigmo on 2009-12-02
I've setup an ubuntu server for a project I'm working on and I connect to it via SSH. I'm finding that there are configuration files I need to print, but I can't figure out how to do so via the command line.
I've got a network printer I can use and I think I can use either the lp or lpr command, but I can't figure out how to specify the printer - either at the command line or as an environment variable.
Any assistance or a point in the right direction would be appreciated.

---

### Post by Bag-O-Stuff on 2009-12-02
You need to get a printer set up.  You can add them from the command line, but you might find the web page cups comes with much easier.  It only listens on localhost so you might not be able to get to it remotely.  If you can, change /etc/cups/cupsd.conf:

```
Listen localhost:631
```

to

```
Listen *:631
```

This is not secure so put it back when you are done.  Have cups reread it's config file:

```
killall -HUP cupsd
```

Then browse to your server on port 631:

```
http://yourserverhere:631
```

Go through the steps of adding the printer.  Once done, you can print from the command line through a number of methods.  Catting a file is simple:

```
cat myfile.txt | lpr -P mynewprintername
```

If you don't want to or can't go through the web interface, do a man on lpadmin.

---

### Post by zigmo on 2009-12-03
Thanks for the info.
I made the changes to /etc/cups/cupsd.conf, but when I tried to access via a browswer, I got, "400 Bad Request," so I changed it back.

I tried the following command:

```
lpadmin -p Accounting_4014 -m hp-laserjet_p4014n-ps.ppd -v "network socket://192.168.59.66" -D "Accounting 4014" -u allow:all -L "Downstairs Accounting"
```

Verifying the -m and -v options from lpinfo, but got the following error (even when running as sudo):

```
lpadmin: Unable to copy PPD file!
```

I originally tried to run the command without the -p option, but got the error:

```
lpadmin: Unable to set the interface script or PPD file:
         You must specify a printer name first!
```

Am I making some simple mistake?

---

### Post by Bag-O-Stuff on 2009-12-03
What are you sending to the printer?  If it's already in PS or PCL format, you don't even need the PPD file.  You also might need to include the port number.  9100 is the Jet Direct port number.

---

### Post by Bag-O-Stuff on 2009-12-03
I tried this on my computer and it adds the printer (I had to use a valid IP address though):

lpadmin -p Accounting_4014 -v "socket://192.168.59.66:9100"

---

### Post by zigmo on 2009-12-04
Thanks - it looks like I was trying to enter too much information.
I followed your suggestion and tried to print via lp and it didn't work. I had to enable the printer via

```
lpadmin -p Accounting_4014 -E

```
and could print .. sorta. When I try to print text files by the following command:

```
lp -d Accounting_4014 testfile
```

It works, except that the output is weird. I get the first line of text, but the second line starts to the right of where the first line ended. I can't even see any subsequent lines that I only assume are too far off the page.

---

### Post by Bag-O-Stuff on 2009-12-07
Depending on what you are trying to print, you might need to do some sort of preprocessing.  Convert to Postscript or PCL.  Plain text files might need a few of the setting changed which can be done on the command line:

[http://www.cups.org/documentation.php/options.html](http://www.cups.org/documentation.php/options.html)

Look in this document for "Lines per Inch" or "Characters per Inch".

You might also try converting your plain text document into Postscript with the command called "enscript".  It works like this:

```
enscript -PAccounting_4014 testfile
```

---

### Post by zigmo on 2009-12-08
Thanks for the help and the CUPS link - both have been invaluable.

I played with re-adding the printer via lpadmin, but this time I tried to specify a PPD file, figuring that if CUPS knew what kind of printer it was printing to, it would be able to handle the output better. Last time I tried, I used the path that the lpinfo -m provided. This time, I used find to search for the file itself. Maybe I don't get something basic, but the find command found the file in a completely different place than lpinfo -m listed it as being.
```

lpinfo - m output
lsb/usr/hplip/HP/hp-laserjet_p4014n-ps.ppd

find output
/usr/share/ppd/hplip/HP/hp-laserjet_p4014n-ps.ppd
```

Once I plugged that into my lpadmin command via -P, lp will now print text files and wrap lines appropriately. The text comes out pretty big, but I'm going to try to figure that out next.

Edit:
I spoke to soon. Lines that are longer than one page width wrap once, but no more than that even if I set -o media=Letter. Back to the drawing board.

---

