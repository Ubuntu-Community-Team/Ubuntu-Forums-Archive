---
title: "Apache2 Minimal?"
date: 2006-11-23
forum: Server Platforms
---

### Post by DannyG on 2006-11-23
Hi,

Is there a way to minimise the amount of load that Apache2 uses on a server? I run a very small website that doesn't get a huge amount of hits, but Apache2 is using a lot of the systems memory and is slowing the whole thing down.

I have complete root access to the server, and I also use Webmin to administer the server.

Note that when I restart Apache2, the server load drops to hardly anything and runs very nicely for about an hour. But then suddenly it shoots back up.

Currently, Apache2 has not been tweaked at all, and everything is running on its default values.

Is there a way to configure and tweak Apache2 so that it will run a lot less heavily?

PHPInfo: [http://www.dannyg.co.uk/info.php](http://www.dannyg.co.uk/info.php)
Status: [http://www.dannyg.co.uk/status/](http://www.dannyg.co.uk/status/)

Any other info you need, let me know.

Thanks,
Daniel.

---

### Post by MJN on 2006-11-23
Seems strange it's using so many resources... I run a 1GHz PIII-based server and wouldn't notice any difference whether Apache were running or not - even with multiple accesses to it at the time.

What indications are you getting that Apache is consuming resources? And do you know what it's doing at the time? Is anyone accessing it? (iptraf is a nice simple tool to see who's connected at any one time)

Mathew

---

### Post by DannyG on 2006-11-23
I know its Apache2 thats using the resources, because when I shut it down the Memory Usage falls to about 35% and the Swap Usage drops to 0%. I then start Apache2 back up, and the Memory Usage stays about 40-50% and the pages load no problem, but after a couple of hours the load just hits the roof.

I presume its doing it all the time, becuase whether I check it on the morning, afternoon, night, evening, different computers, it always shows the same load and takes the same amount of time to load pages.

I run IPTraf and the screenshot is attatched. After taking the screenshot, a few more IP's appeared on the list with high 5 digit ports, the top IP there is my server IP, and the 2nd one is my routers IP.

Daniel.

---

### Post by MJN on 2006-11-23
Be very careful trying to determine anything from 'memory usage' - memory is such a complex area that it's not possible to assume how much memory is actually 'in use'. However, notwithstanding this, are saying that pages are slow to load during these high peak times?

Looking at your IPTraf screenshot, if 63.99.9.2 is your server's IP then that is simply an SSH connection (port 22) from 86.135.230.106 - I'm guessing you've SSH'd into your server from there (if not, someone has!)? If it is you, the reason the numbers keep escalating is because it's measuring traffic on that connection.... to update the figures requires traffic to be sent hence this is a vicious circle... all perfectly normal however.

The other connections are to other computers - an SMTP connection to a mail server on 63.76.232.56 and an HTTP connection to a web server at 63.76.232.152.

Hence, at the time of the screenshot no other connections to your server (other than your SSH connection) were present.

I'm still unclear what the symptoms are here - other than memory usage (where are you getting that info from?) what is telling you that server load is high? For what it's worth, access to the server (website) seems quick enough from here.

Mathew

---

### Post by DannyG on 2006-11-23
My status script [http://www.dannyg.co.uk/status/](http://www.dannyg.co.uk/status/) is telling me the memory load is high.

I've just amended a few configuration options after googling a bit and restarted the server to see if that makes a difference, which is why its loading ok for now. I'll give it a few hours and see if it holds the same speed.

Daniel.

---

### Post by MJN on 2006-11-23
What does it mean by 'memory load' though?

As I said, monitoring memory usage is a complex area - it's far more involved than what can be represented by a simple percentage figure.

I can't help feel you're looking for a solution to a problem that doesn't exist... and that the only reason you think you've got a problem is because the 'memory load' bar seems pretty high?

Would that be a fair assesment? (Feel free to refute it; I'm not having a go! :))

To perhaps illustrate with an example, here's the output of the **free** command on my system (all figures in KB):

[FONT=Courier New][B]-----total--used---free--shared-buffers-cached
Mem:        516124     485052      31072          0      12824     137684
-/+ buffers/cache:     334544     181580
Swap:      1048816      40212    1008604[/B][/FONT]

As you can see, I have 516MB total of which 485MB is being used leaving me with 31MB free. You might deduce from this that my system is a nat's ball from falling right over... but it's not... it's flying like sh1t of a shovel. Furthermore, other than me tapping away the system is pretty much just sat here at the moment (of course numerous ongong process behind the scenes, and X etc, but no downloads/torrents/uploads/backups/virus scans/mail delivery etc currently taking place). The figures alone are not easy to translate into a real-world indication of available performance - and a bar chart with unknown origin is chocolate teapot territory.

Mathew

(P.S. Forgive the liberal metaphor/phrase usage there - but as you're a Brit they hopefully make sense! ;))

---

### Post by DannyG on 2006-11-23
My problem is also based on the fact that it takes 3-5 seconds for me to connect to my website when the memory load is high, so the problem definitely does exist.

But like i said, i've edited some config files and am waiting an hour to see if the same problem arises.

---

### Post by MJN on 2006-11-23
Okay. Let's keep going then!

What have you changed?

Mathew

---

### Post by tturrisi on 2006-11-23
We already coverd this in your other post.
[http://www.ubuntuforums.org/showthread.php?t=300871](http://www.ubuntuforums.org/showthread.php?t=300871)

1. the server does NOT have enough ram to begin with, only 256 total ram on that server.
2. something(s) misconfigured on the server too.
3. you have a lot of server services running for that amount of ram.
4. possible hardware misconfigs too.

For one thing, that status program consumes memory & resources.  Best to monitor the server status from a different computer using something like Conky or gKrellm.  That delay in page load can be caused by misconfig'd apache or even misconfig'd networking, or the host's network (company who sells the server net) itself is not setup correctly or setup w/ cheap hardware.

---

### Post by MJN on 2006-11-23
The memory usage (whatever that is) is showing 40% so how can that be considered a problem?

As mentioned, I'm using 485MB out of 512MB - are you saying I'm short of RAM and hence should be suffering permorance issues? I can categorically tell you I'm not...

The REAL problem here is trying to read anything into a pretty graphical 'stats' page where absolutely no information is given as to how measurements have been taken.

Mathew

---

### Post by DannyG on 2006-11-23
I changed the StartServers, MaxSpareServers, MinSpareServers, MaxClients, KeepAliveTimeout etc, and it seems to be doing the job.

256MB RAM is more than enough to run a very small webserver...

---

### Post by MJN on 2006-11-23
I completely agree - 256MB is plenty sufficient particularly given the relatively low connection count.

However, for this very reason I really don't see the need for you to need to try and get your config any leaner.

Most of the directives you've mentioned are normally dynamically self-set in accordance with the current load - and indeed statically setting them is usually only advantageous when supporting multiple concurrent connections (and by multiple I'm talking hundreds if not thousands).

Given you said the connection count is low I am highly suspect that any perceived performance increase you may have seen is a direct consequence of the majority of those settings you've specified. I'm not saying you're lying, but rather that it doesn't make sense.

Mathew

---

