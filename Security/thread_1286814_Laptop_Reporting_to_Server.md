---
title: "Laptop Reporting to Server"
date: 2009-10-09
forum: Security
---

### Post by dbrooke on 2009-10-09
Hello,

I recently bought an expensive laptop and have been thinking about another way to protect it by using a crontab and curl to report to my central webserver ever hour. On the webserver, I have a landing app that will record info. However, this is where getting some opinions from you all will help.

First, besides IP address, is their any other info that could be gleaned from a shell script that would be useful to send to the central server? I know one can get a fairly accurate picture of where an IP ADDRESS originates from, and in a theft situation, I think very accurate information could be attained. However, I thought I'd see if I should be including other information.

Second, if a computer is off-line, I am assuming a cron-tab/curl will not clog up processes by trying to reach the central server but being unsuccessful. This may be a bad assumption. :-)  Any comments on that?

Thanks!

Donovan

---

### Post by Sarmacid on 2009-10-09
If your laptop has a webcam you can get pictures also.

---

### Post by cariboo on 2009-10-09
If you have built-in gps, it could also send you a location.

---

### Post by __p1n__ on 2009-10-09
It's evocative of a loser of a Mac app called Undercover.  The application that you mention suffers from a common design vulnerability to that Mac app.  Any non-idiot thief will either wipe the disk if they want to use it or sell it, or; start it up with a live image of some sort if they want to rummage through your data.

Either way the app installed on the laptop will not be running and consequently all that you'll get from it is the fact the stop in recorded server log entries corresponds to the time that you lost the laptop.

If you want to relabel it and call it "catch-your-idiot-buddy-who-nicked-your-laptop" then it might get some traction.

A better approach would be to insert the "boomerang" type app to the network interface firmware however the actual execution of that would be quite challenging I think.

---

### Post by cariboo on 2009-10-09
You're assuming the thief knows more about computers than just turning it on and using msn or word. In my area most thieves are barely literate, let alone computer literate. All they know is they can get $50.00 for it if they sell it before they get caught.

---

### Post by dbrooke on 2009-10-10
Thanks for the comments.
Yes to a web cam, no to GPS. This is a MacBookPro17... hope the question here on the ubuntu forum is O.K. I always get better answers here.

Since the landing page I built only records the public I.P. address.. I was able to get at (and pass) the internal I.P. as well by doing:

ifconfig en1 | grep "inet " | awk '{print $2}'

(not that this would be very helpful in the real world) ;-)

I understand that it is very likely that this kind of thing would never be useful.. but I'm in a situation where it will only take a few minutes to create this... so.. why not. ? 

I did some googlefu about the WebCam SnapShot idea.. but no luck with an iSight command line to trigger such a thing.

Ah Well, IP address/s only I guess.. moving forward.

Thanks for the comments.

Donovan

---

### Post by Jive Turkey on 2009-10-12
There is an app called prey that will do those things (including the webcam).  There are Linux, windows and mac versions.  It suffers from the same flaw described above (destroyed by disk format).  It seems to me it would be most effective if you had an unpassworded honeypot account to distract the thief while you gather the info.

[http://preyproject.com]("http://preyproject.com")

Also, it might help to password protect your BIOS and set the HDD as the only boot option in your bios making it impossible to boot from CD or USB without either flashing the bios or knowing the password.

---

### Post by Lars Noodén on 2009-10-12
@ Donovan : you can use traceroute to find the way home from the laptop, and presumably the way to the laptop.  Substitute the IP number of your http server for **74.125.79.99** below.  You might consider using https instead of http so that it gives less away.  

[INDENT][FONT="Courier New"]traceroute -n **74.125.79.99**  | curl --data-urlencode traceroute@-  [http://**74.125.79.99](http://**74.125.79.99)**/cgi-bin/x.pl[/FONT][/INDENT]

This passes the result of traceroute to the web server.  See the curl manual page for more details on the --data option.  The use of -n speeds things up by eliminating the need for DNS lookups, which may also risk detection.  Use the IP# for your server for the same reason plus it increases reliability in case of unreliable DNS where the laptop happens to find itself.  

There above has 1 weakness, it can be called until your log space fills up, which may or may not be a problem depending on your partitioning.  Or if you are using log rotation, until the logs are rotated out, losing the data.  One way, of several, to prevent that would be a more complex version would only allow pgp-signed http POSTs.

On the server side, you need a simple script to collect the data.  Something like this works for perl, you can use python or c or c++ or java:

```
#!/usr/bin/perl -w

use integer;
use strict;
use CGI::Simple;

##
##

my $logfile = qq(/var/tmp/traceroute.log);      # log goes here
my $cgi = new CGI::Simple;      # new CGI object

# some visible response to the web client
print qq(Content-type: text/plain\n\n);
print qq(Hello, World\n);

# set umask for output, 0222 is -rw-r--r--
umask 0022;

# open log file for appending
open ( LOG, ">> $logfile" )
    or die ( "Could not open '$logfile' : $! \n");

# get the server's local time
my ( $sec, $min, $hour, $day, $mon, $year) = localtime;

# start log entry with a time stamp
printf LOG qq(%d-%02d-%02d %02d:%02d:%02d \n),
    $year+1900, $mon+1, $day, $hour, $min, $sec;

# load and print the value of the field traceroute
print  LOG $cgi->param('traceroute'), qq(\n);

close ( LOG )
    or die ( "Could not close '$logfile' : $! \n");

exit (0);

```

---

