---
title: "IIS passthrough to Apache"
date: 2007-09-13
forum: Server Platforms
---

### Post by insanity2k7 on 2007-09-13
I have an interesting predicament on my hands and wanted to see if anyone knew what I was missing.  Long story short, our Ubuntu server began life as a MS/SA/MW/CAV box.  The boss loves watching MailWatch all day and recently decided he'd like to be able to watch it at home too...

I moved all but one of the web sites off of our Win2k3 server over to the Ubuntu server.  I changed the port forwarding to the Ubuntu server and that was that -- until today.  It was discovered that Outlook Web Access (OWA, aka Exchange Webmail) doesn't work.  Since OWA needs to be available to the sales folks, I had to immediately switch forwarding back to the Win2k3 server.

Now everything works except MailWatch.

I added SMB to the Ubuntu server and it verified everything works.  I created a new web site in IIS and pointed its path to \\server\mw-web-dir.  I can access MailWatch by [http://server/mw-web-dir](http://server/mw-web-dir).  I cannot access MailWatch using [http://mailwatch.domain.com](http://mailwatch.domain.com).  I get as far as login credentials being requested and here's what I've figured out...  the credentials requested end up being passed to the IIS server and they seem to stop there.  MailWatch requires a login, but before I freaked out I decided I would try the same thing with MailScanner-MRTG.  Even though MRTG is setup as an anonymous access web site, I get the following error when connecting:

Directory Listing Denied
This Virtual Directory does not allow contents to be listed.

I can pull up MRTG via SMB without providing credentials.  However, I cannot pull up MailWatch in the same way although I think that's because MW is in PHP (without the server running the "script" it won't work regardless, right?).  The only simple answer I've been able to arrive it is obtaining a second public IP but since we're using less than desirable equipment, we aren't going to be able to pull that off short of buying new gear.

Ideally, there will be some method where I can use the IIS server, connect to the Ubuntu server across SMB and virtual directories, and somehow have people access username restricted websites from outside.  Thanks in advance for any help you may have to lend.

---

### Post by insanity2k7 on 2007-09-14
In a brief moment of ASTONISHING -- ASTONISHING I say -- brilliance...  I have found the answer to this problem!!!  I only hope this solution goes on to help others...  but it's actually very simple.

First you have to get SMB working which is pretty simple really...  but just for the sake of being complete, here's a sample /etc/samba/smb.conf:

[I][global]
workgroup = MSHOME #This can be anything you want
netbios name = SERVERNAME
security = share
auth methods = guest
domain master = no
wins support = yes

[mailscanner]
path = /var/www/mailscanner
read only = no
guest ok = yes

[mrtg]
path = /var/www/mailscanner-mrtg
read only = no
guest ok = yes[/I]

In this example, "mailscanner" and "mrtg" are the sharenames.  This is literally all you need for your smb.conf.  On a side note...  when you make changes you need to do this:

/etc/init.d/samba reload
/etc/init.d/samba restart

The first line reloads your configuration file and the second line stops the SMB service and restarts it using your new config file.  At this point you should be able to map your shares.  In my case, \\servername\mailscanner showed me exactly what I wanted to see so I moved on to the next stuff.  The next step in my mind was setting up the virtual directory in IIS, which is what I did, and I created it with the host header "mailwatch.domain.com"  At this point I was stuck until just now.

All you have to do is edit /etc/apache2/httpd.conf for the host header value you assigned in IIS.  For example, in my case I setup a host header of "mailwatch.domain.com" for the mailscanner page.    Basically you want the host headers to match on the IIS side and on the Apache side, and here's all you do.  Here's a sample /etc/apache2/httpd.conf file:

<VirtualHost *>
  ServerName mailwatch.domain.com
  DocumentRoot /var/www/mailscanner
</VirtualHost>

After you add that:

/etc/init.d/apache2 reload
/etc/init.d/apache2 restart

The lines here do the same thing they did with the SMB daemon.  That is it.  I pat myself on the back because I actually figured this one out on my own.  YAY ME!  I was playing Saints Row taking a brain break when it came to me.  I tried it, it works and it'll most likely work for you too.

---

### Post by insanity2k7 on 2007-09-14
Well don't I feel like a jackass...  I was so excited over NOTHING.  At some point along the way I forgot to change port 80 forwarding from the Apache box back to the IIS box...  On the bright side I s'pose I learned how to setup virtual folders on an Apache box.  /sigh

So anyway...  :confused:

---

