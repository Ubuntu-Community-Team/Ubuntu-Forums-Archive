---
title: "rtorrent, apache, and conky in Ubuntu"
date: 2010-09-01
forum: Tutorials
---

### Post by grandsatrap on 2010-09-01
I've been working off and on for 3 days trying to get **rtorrent** working with **apache**. I had to
piece together a number of other websites which refer only to ArchLinux and lighttpd. 

Why?
Rtorrent is a small lightweight easy to use torrent client.
Apache is a common webserver and is already installed (when you set up a LAMP server). I don't want to install another webserver (lighttpd).

rtorrent can send and receive information through XMPLRPC ports. However, this requires being handled by a webserver (hence Apache). 
Scripts can be written to access the XMLPRC information from Apache. The one I found on the internet uses Perl with the Frontiers module. This script outputs data in a format that conky can handle.

**[COLOR="Red"]Please note, Ubuntu commands that you type at the command line are in red.[/COLOR] Code that is not red is either what you need to enter into your editor or is the printed result of the commands typed.**
**Steps:**
1. Install rtorrent
```
sudo apt-get install rtorrent
```

Create directories (or folders): torrents, session
I assume that your scripts are stored in a directory called "scripts" i.e. $HOME/scripts

2. Edit .rtorrent.rc  . I have just put the bare necessities in to get rtorrent working. (I use vi, but you can use another editor)

```
[COLOR="Red"]vi $HOME/.rtorrent.rc[/COLOR]

#my .rtorrent.rc file
directory=$HOME/torrents
session=$HOME/session
peer_exchange=yes
scgi_port = 127.0.0.1:5000
```


Try rtorrent and see if it works. See **[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)**
(Learn how to use screen. It is great for running things like rtorrent on a headless server).

3. Install xmlprc  (if you type "xmlrpc" at the command-line it will tell you how to download it)
```
[COLOR="Red"]sudo apt-get install libxmlrpc-c3-dev[/COLOR]
```

4. Install the scgi module to apache (I assume that apache is already installed and running)
```
[COLOR="Red"]sudo apt-get install libapache2-mod-scgi
sudo a2enmod scgi
sudo /etc/init.d/apache2 force-reload[/COLOR]
```

5. Now edit the sites-available in apache:
```
[COLOR="Red"]sudo vi /etc/apache2/sites-available/default[/COLOR]
```
These are the last lines of this file. You can see where I've inserted stuff.
I got this from [COLOR="Blue"][http://transdroid.wordpress.com/download/using-rtorrent-on-ubuntu/](http://transdroid.wordpress.com/download/using-rtorrent-on-ubuntu/)[/COLOR] which has extra 
stuff on how to secure your xmlrpc port. I didn't bother since access is only allowed on my LAN.

```
#insert these for rtorrent xmlrpc
SCGIMount /RPC2 127.0.0.1:5000
<location /RPC2>
AuthName "rTorrent secure access"
AuthType None
</location>
#end of insert
</VirtualHost>

```
Restart Apache:
```
[COLOR="Red"]sudo /etc/init.d/apache2 restart[/COLOR]
```

6. Now you can test it. Type this in:
```
[COLOR="Red"]xmlrpc localhost d.multicall "main" "d.get_base_filename=" "to_mb=\$d.get_bytes_done=" "to_mb=\$d.get_left_bytes=" "to_mb=\$d.get_size_bytes=" "to_kb=\$d.get_down_rate="
[/COLOR]

```You'll see something like:
Result:

```
Array of 1 items:
  Index  0 Array of 5 items:
             Index  0 String: 'Sliding.Doors.(1998).DVDRip.ENG-BlicaDePreto'
             Index  1 String: '   307.8'
             Index  2 String: '   400.0'
             Index  3 String: '   701.0'
             Index  4 String: '289.9'


```You can also type in commands like:
```
[COLOR="Red"]xmlrpc localhost get_down_rate[/COLOR]

Result:

Integer: 298385
```

7. Now add a script to take the XMLRPC output and make in into something that Conky can use.
I modified the script from [COLOR="Blue"][http://www.sakana.fr/blog/2009/10/11/conky-integrating-rtorrent-downloads-monitoring/](http://www.sakana.fr/blog/2009/10/11/conky-integrating-rtorrent-downloads-monitoring/)[/COLOR]
Unfortunately it requires a Perl module to be installed:

```
[COLOR="Red"]sudo apt-cache search perl frontier::RPC
sudo apt-cache search perl frontier::client
sudo apt-get install libfrontier-rpc-perl[/COLOR]

```

8. Now install the script
```
[COLOR="Red"]vi ./scripts/rtorrent.status.pl[/COLOR]
```

```
#! /usr/bin/perl

use strict;
use warnings;

use Frontier::Client;

#test if rtorrent is running (you can just use $HOME/session for the session directory)
my($sessdir)='/home/foooo/session';

if (! -e "$sessdir/rtorrent.lock")
{
   printf("\${color FFFFFF}Rtorrent not running\n");
   exit;
}

# Configuration
use constant server     => 'http://localhost/RPC2';

# Do not edit below this comment
my $server = Frontier::Client->new(url => server);

my $uprate = $server->call('get_up_rate');
my $downrate = $server->call('get_down_rate');

my $torrents = $server->call('d.multicall', "main",
"d.get_base_filename=",
"d.get_bytes_done=",
"d.get_size_bytes=",
"d.get_down_rate=");

my @res;
foreach my $d (@$torrents) {
        my $dl_rate = $d->[3] / 1024;
        my $percent_done = 100 * ($d->[1] / $d->[2]);
        push @res,
        sprintf("%.28s \${alignr}%6.1f kB/s\n" .
        " " x 2 . "%3.2f%%" . " \${execbar echo %3.0f }",
        $d->[0], $dl_rate, $percent_done, $percent_done);
}

printf("\${color 33DD55}%6.1f kB/s up / %6.1f kB/s down\n \${color 33AA44}", $uprate / 1024, $downrate / 1024);
print join("\n", @res), "\n";
```


9. Test it:
[COLOR="Red"]./scripts/rtorrent.status.pl[/COLOR]

You'll see output like this (assuming that rtorrent is running)
```

   0.2 kB/s up /   84.8 kB/s down
Sliding.Doors.(1998).DVDRip.ENG-BlicaDePreto ${alignr}  84.5 kB/s$alignr
     48.63%${goto 70}${execbar echo  49 }
```


10. Add the following to .conkyrc (i.e. vi .conkyrc from your home directory)
```
{execpi 10 $HOME/scripts/rtorrent.status.pl}
```

Make sure that you also add "text_buffer_size 1024"

Voila!

11. If you have a headless server (makes sense), then show conky on your Linux laptop/desktop 
by typing
```
[COLOR="Red"]ssh username@192.168.1.7 -X [-p 2345 -i mykey.ppk][/COLOR]
```
Where 2345 is your SSH port and mykey.ppk is your private key.
You can also get this working from Windows if you run XMING on your windows computer (Google "download xming").


12. Since we have all of this done why not add wutorrent to have a GUI control for rtorrent? This will be my next step.

---

### Post by grandsatrap on 2012-02-27
Here is a better image of conky working with rtorrent

---

### Post by grandsatrap on 2012-02-27
... much later

Actually, I never bothered improving this. I don't need a GUI control for RTORRENT -- that would just defeat the purpose of a CLI torrent client.  I am now quite comfortable with using the commands for rtorrent.

The only bug that I've found is that the % doesn't always display properly. This happens when I am only downloading one large file from a torrent. I think something gets confused between the % of the file that's downloaded and the % of the whole torrent.

---

### Post by pyroscope on 2012-03-07
Mine is quite similar, which is not surprising, since there is only so much sensible values to display...

[IMG]http://pyroscope.googlecode.com/svn/trunk/pyrocore/docs/examples/conky-rtorstat.png[/IMG]

---

### Post by grandsatrap on 2012-08-08
>>>>**FIXED: %downloaded being wrong or even negative!** <<<<

Use the  "to_mb" conversions built into xmlrpc as it's much easier than writing your own conversions in Perl. For large files, xmlrpc returns an INT that is too large, so wraps around and becomes negative, resulting in weird and wrong % downloads.

Make the change in the code, so it looks like this:

```
my $torrents = $server->call('d.multicall', "main",
"d.get_base_filename=",
"to_mb=\$d.get_bytes_done=",
"to_mb=\$d.get_size_bytes=",
"d.get_down_rate=");

```

So the final **rtorrent.status.pl** code is:

```
#!/usr/bin/perl

use strict;
use warnings;
 
use Frontier::Client;

#test if rtorrent is running
my($sessdir)='/home/adelaide/rtorrent/session';

if (! -e "$sessdir/rtorrent.lock")
{
   printf("\${color FFFFFF}Rtorrent not running\n");
   exit;
}

# Configuration
use constant server => 'http://localhost/RPC2';
 
# Do not edit below this comment
my $server = Frontier::Client->new(url => server);

my $uprate = $server->call('get_up_rate');
my $downrate = $server->call('get_down_rate');

#use the "to_mb" conversions built into xmlrpc as other conversions are messy
#for large files, it returns an INT that is too large - wraps around and becomes negative.
my $torrents = $server->call('d.multicall', "main",
"d.get_base_filename=",
"to_mb=\$d.get_bytes_done=",
"to_mb=\$d.get_size_bytes=",
"d.get_down_rate=");

my @res;
foreach my $d (@$torrents) {
	my $dl_rate = $d->[3] / 1024;
	my $percent_done = 100 * ($d->[1] / $d->[2]);

if ($percent_done == 100) {	
	push @res,
	sprintf("\${color 0033FF}%.28s \${alignr}%6.1f kB/s\n" .
	" " x 2 . "%3.1f%%" . " \${execbar echo %3.0f }\${color 33DD33}",
	$d->[0], $dl_rate, $percent_done, $percent_done);
} else {
	push @res,
	sprintf("%.28s \${alignr}%6.1f kB/s\n" .
	" " x 2 . "%3.1f%%" . " \${execbar echo %3.0f }",
	$d->[0], $dl_rate, $percent_done, $percent_done);
}
}

printf("\${color FFDD33}%6.1f kB/s up / %6.1f kB/s down\n \${color 00AA00}", $uprate / 1024, $downrate / 1024);
print join("\n", @res), "\n";

```

---

