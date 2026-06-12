---
title: "Running cups without web interface"
date: 2009-05-12
forum: Server Platforms
---

### Post by mbeach on 2009-05-12
I'm sure this has been asked and answered, but I cannot seem to find an answer.  I see a request on the brainstorm site but no definitive answer.

I've got a print server running (cups only no samba) which is world accessible on port 631.  That is fine and dandy, but I would like to shut down the web interface (do everything from command line anyway).  I'm not sure if its possible while allowing the clients access to the printers.  I know the admin is restricted, but I'd like to eliminate the various customers from seeing the full printer list.  I thought that the BrowseAllow directive did that but it does not seem to be the ticket.

The printers are actually just scripts which take in some raw print files overnight (old legacy systems - only real way to get the data out is to print).  I've got a number of customers and I have a printer set up for each in order to identify them.  I know I can setup authentication etc, but if I can avoid that for now, that would be advantageous.

---

### Post by lykwydchykyn on 2009-05-13
That's a good question.  I don't see a way to do it, unless I'm missing something, though I don't quite grasp the meaning of some configuration terms.

I see where you can add an additional port for running the admin interface, but it still runs on the old port as well.

I'll be interested to see if anyone comes up with an answer.

---

### Post by theozzlives on 2009-05-13
You should be able to cut web access to your computer in your router setup.

---

### Post by lykwydchykyn on 2009-05-13
> **theozzlives said:**
> You should be able to cut web access to your computer in your router setup.

The OP is talking about the CUPS HTTP interface, which runs on the same port as the printing service itself (631).  If you just cut off 631, you cut off printing as well as the printer admin interface.  OP just wants to cut off the admin (HTTP) interface, not printing.

---

### Post by mbeach on 2009-05-14
Outside of doing some cgi patches I can't find a way.  Looking at:
[http://www.cups.org/str.php?L2625+P0+S-2+C0+I0+E0+M20+Q2625](http://www.cups.org/str.php?L2625+P0+S-2+C0+I0+E0+M20+Q2625)

perhaps an option will roll out in version 1.5.

Thanks.

---

### Post by cariboo on 2009-05-14
If you haven't changed any configuration files, the cups web interface is only available from the computer it is installed on. No one else can access it.

---

### Post by mbeach on 2009-05-14
> **cariboo907 said:**
> If you haven't changed any configuration files, the cups web interface is only available from the computer it is installed on. No one else can access it.

But in that case, no one else can print to the printers either (as I understand it).  I believe you may be talking about the listen directive which by default is Listen localhost:631, however, in my case I'm trying to share several printers, making them world accessible, so have to remove that directive, and replace with the "port 631".

Also, leaving the <Location /> in default form prevents remote people from connecting to the printers.

As it stands now, with the version I'm using 1.3.9 the web interface comes right along with allowing remote printing.  I am not using samba in any fashion (this is a bare bones minimal setup) designed only to act as a place to receive print files to be subsequently massaged/mined.

Thanks though.

---

