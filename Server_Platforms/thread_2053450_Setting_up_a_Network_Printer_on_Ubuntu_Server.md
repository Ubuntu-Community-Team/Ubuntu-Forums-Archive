---
title: "Setting up a Network Printer on Ubuntu Server"
date: 2012-09-05
forum: Server Platforms
---

### Post by SeaHawk22 on 2012-09-05
I am very new to servers. I recently setup a Ubuntu server, and I want to attach a printer to share on my home network. The server is up in running in the sense that I can log in through SSH. I edited the smb conf file as directed by tutorials I have read (so the workgroup matches). I have also edited the smb conf file on my desktop as well. Surprisingly I cannot find a detailed tutorial on what to do next. I assume that I need to install the drivers on both systems server/desktop. I was able to locate Linux print drivers, but I am little lost on what direction to go next. Does anyone know of a decent tutorial I could follow?

Thank you,

---

### Post by SeijiSensei on 2012-09-05
First off, you need to be running CUPS on the server which is the printing management system used on Unix machines.  So check to see if it is running like this:

```
ps ax | grep cups | grep -v grep
```

If that comes up empty, then run:

```
sudo apt-get install cups
```

If it says that CUPS is already installed, then try 
```

sudo service cups start
sudo chkconfig -s cups

```

I recommend reading this part of the Ubuntu Server Guide before you start: [https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html)  You will need to change the Listen directive if you want to print over the network.  Follow the instructions in the Guide.  Once you are done, try printing a test page from the CUPS manager.  Now I would reboot the server just to ensure everything comes up as required and works together correctly.  Print another test page to make sure.

Now go to a client machine and see if you can access the printer.  On a Windows box you should be able to use the "\\server\printername" naming scheme.  If you're using Ubuntu clients, you should run the printer configuration tool that comes with Ubuntu, or you can use the same [http://localhost:631/](http://localhost:631/) URL on the client machine to talk to CUPS.  (If CUPS is not running, follow the steps above.)  You have two choices to connect to the remote printer.  You can use the ipp:// style connection that will talk directly to CUPS, or you can use an "smb://server/printername" URL to connect via Samba. Pick the correct driver and try printing a test page.

---

### Post by LHammonds on 2012-09-06
I simply used a Zentyal server as my print server.  I tried to setup CUPS by hand on an Ubuntu server but failed miserably.  Didn't take very long at all to get a print server setup using Zentyal.

LHammonds

---

### Post by lykwydchykyn on 2012-09-06
Assuming you have cups installed, just point a web browser to port 631 on your server's IP and you'll find a decently friendly interface for setting up a printer.

---

