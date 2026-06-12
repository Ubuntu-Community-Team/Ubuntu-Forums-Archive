---
title: "All I want is a simple IP printer"
date: 2008-10-23
forum: Server Platforms
---

### Post by edpatterson on 2008-10-23
All I really need to the ability to print text files to a network printer. I thought it would be simple but the more I read the more confused I get.

**famous last words**
[LIST]
[*]X is not, nor will it be loaded on my servers 
[*]I do not need to print pictures
[*]Only admin types will have access to the servers
[/LIST]

Is there any brain dead, text mode, universal printer configuration commands? I have Cannon (Ricoh under the hood), HP, Lexmark and Ricoh printers at my disposal. I would prefer directions for an HP as that would keep me from getting any of that dreaded stuff called exercise.

I bought the Sams Ubuntu Unleashed book because back in the day the Unleashed books were the best choice. It seems the days have changed and I am now looking for a good ***book*** (I read in bed) that covers the all the common things from the console point of view. 

Thanks for any help or pointers to help.
Ed

---

### Post by anystupidname on 2008-10-23
Perhaps some of these will help?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[http://howtoforge.net/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://howtoforge.net/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server)
[http://howtoforge.net/ipp_based_print_server_cups](http://howtoforge.net/ipp_based_print_server_cups)
[http://wiki.samba.org/index.php/Samba_as_a_print_server](http://wiki.samba.org/index.php/Samba_as_a_print_server)

---

### Post by koenn on 2008-10-23
> **edpatterson said:**
> All I really need to the ability to print text files to a network printer. I thought it would be simple but the more I read the more confused I get.

**famous last words**
[LIST]
[*]X is not, nor will it be loaded on my servers 
[*]I do not need to print pictures
[*]Only admin types will have access to the servers
[/LIST]

Is there any brain dead, text mode, universal printer configuration commands? I have Cannon (Ricoh under the hood), HP, Lexmark and Ricoh printers at my disposal. I would prefer directions for an HP as that would keep me from getting any of that dreaded stuff called exercise.

I bought the Sams Ubuntu Unleashed book because back in the day the Unleashed books were the best choice. It seems the days have changed and I am now looking for a good ***book*** (I read in bed) that covers the all the common things from the console point of view. 

Thanks for any help or pointers to help.
Ed

Some printers do lpd, i.e. they listen on port 515/tcp for printjobs.
With a bit of luck, any text you send there will just get printed  :)
you'll need to do some configuration on your server, like creating devices where you redirect output to if you want it printed. I have no idea how that's done.

---

### Post by edpatterson on 2008-10-24
> **anystupidname said:**
> Perhaps some of these will help?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[http://howtoforge.net/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://howtoforge.net/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server)
[http://howtoforge.net/ipp_based_print_server_cups](http://howtoforge.net/ipp_based_print_server_cups)
[http://wiki.samba.org/index.php/Samba_as_a_print_server](http://wiki.samba.org/index.php/Samba_as_a_print_server)

Thanks, whilst none of the links had the definitive answer, they did lead me to the actual cups documentation. Why I did not start there is beyond me, old I guess.

I tried
```

# /usr/sbin/lpadmin -p EdsLaser -E -v socket://192.168.1.100 -m laserjet.ppd

```
which according to the docs is all I needed. The command returned
```

Unable to copy PPD file!

```
I tried 'locate ppd' and saw that only Savin, Sharp and Toshiba ppd's were on the server in the /usr/share/ppd/openprinting/ path.

So, I went looking for the ppd file(s) for HP. This lead me to  [http://packages.ubuntu.com/hardy/hpijs-ppds](http://packages.ubuntu.com/hardy/hpijs-ppds)

There is a blurb at the top about using a package manager to install the package.

Would someone be kind enough to give me the command line to install the hpijs-ppds_2.8.2+2.8.2-0ubuntu8_all.deb package?

Thanks,
Ed

---

### Post by tgalati4 on 2008-10-24
Try as root:

#dpkg -i hpijs-ppds_2.8.2+2.8.2-0ubuntu8_all.deb

Watch in amazement.

---

### Post by edpatterson on 2008-10-24
> **edpatterson said:**
> Thanks, whilst none of the links had the definitive answer, they did lead me to the actual cups documentation. Why I did not start there is beyond me, old I guess.

I tried
```

# /usr/sbin/lpadmin -p EdsLaser -E -v socket://192.168.1.100 -m laserjet.ppd

```
which according to the docs is all I needed. The command returned
```

Unable to copy PPD file!

```
I tried 'locate ppd' and saw that only Savin, Sharp and Toshiba ppd's were on the server in the /usr/share/ppd/openprinting/ path.

So, I went looking for the ppd file(s) for HP. This lead me to  [http://packages.ubuntu.com/hardy/hpijs-ppds](http://packages.ubuntu.com/hardy/hpijs-ppds)

There is a blurb at the top about using a package manager to install the package.

Would someone be kind enough to give me the command line to install the hpijs-ppds_2.8.2+2.8.2-0ubuntu8_all.deb package?

Thanks,
Ed

[COLOR="Red"]More info[/COLOR]
I downloaded the .deb file and ran the dpkg command from the same directory. It ran to completion and restarted cupsd

I then tried the lpadmin command and it failed with the same 'Unable to copy PPD file!' error

All commands were issued as root.

Ed

---

### Post by tgalati4 on 2008-10-24
I would find another machine with a browser that is connected to the local net and set up the printer using CUPS web-based administration client.  It's not difficult:

[http://your.print.server.ip:631/](http://your.print.server.ip:631/)

HP printers are generally well-supported, but they use a bundled-driver (several printers mashed into one driver).  CUPS can often detect the printer and pick the correct driver automatically.  How to do this on the command line is beyond my experience.

---

### Post by edpatterson on 2008-10-24
> **tgalati4 said:**
> I would find another machine with a browser that is connected to the local net and set up the printer using CUPS web-based administration client.  It's not difficult:

[http://your.print.server.ip:631/](http://your.print.server.ip:631/)


That is exactly what I have been doing <grin>.

It gets better. From a putty session I went into the /etc/cups directory to triple check my cups.conf file. I found a new printers.conf file. The IP Address for the printer was hosed. I fixed it, saved the changes and restarted cupsd. Next I went back to the web-based admin page, click on the printers tab and my printer was listed. It is shown using the 'local raw printer' driver but the test page with it's gradient fills printed ok.

Just incase someone else is reading this thread trying to do the same thing.

/etc/cups/printers.conf
```

<Printer EdsLaser>
Info EdsLaser
DeviceURI socket://192.168.1.100
State Idls
StateTime 1224849525
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

I have no idea which steps of my trial and error approach created the printers.conf file.

I do appreciate all the help I have received here. When I get the time I will duplicate the process and post only the necessary steps.

Ed

---

### Post by tgalati4 on 2008-10-25
There is a bug in older versions of CUPS/Ubuntu for some HP printers that need to be set up as a RAW print queue on the remote machine (say someone's workstation).  On the server machine, the printer is set up as a locally-connected HP using the appropriate model number.

On HP, Jet-Direct or direct IP-connected printers, you need the correct HP model driver on your workstation to communicate directly with the printer.  No printer server is involved in this case.  You can set up a queue on a print server for a direct-connect network printer and in that case, I think you still need the appropriate driver.  It can get confusing.

This RAW printer bug bit me a while ago.  There should be some logic to provide a warning or at least suggest trying RAW print queue.  My machines are running Dapper through Gutsy, so I can't say if this has been fixed.

---

