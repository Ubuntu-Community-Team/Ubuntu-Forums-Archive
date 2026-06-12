---
title: "NTP: offering the time service?"
date: 2006-10-30
forum: Server Platforms
---

### Post by unless on 2006-10-30
On a Dapper 6.06LTS server, I'd like to set up an NTP server for all of our other servers to use to set their time. Simply doing an "aptitude install  ntp-server" didn't do it: ntpd is running, and keeping this server's clock up to date, but it's not listening on port 123.

I've looked around for a howto on this subject, but I must be using the wrong keywords/search strings. Could anyone please point me in the right direction or give me some basic info on what my ntp.conf needs to look like in order to offer the time service?

Thanks in advance.

---

### Post by am4c130d on 2006-11-30
I am no NTP expert, but think I understand what you are trying to do - as they are the same goals I had...  I only came across this question as I was looking for other NTP answers myself and noticed a lot of unanswered questions that I think I have battled through successfully.

The NTP documentation is phenomenal, but far too long, too complex and way beyond what I needed - but here is a link in any case.  It makes good casual reading, and as you progress more and more will be valuable - or at least that is how I have found it.

[http://www.eecis.udel.edu/~ntp/ntp_spool/html/index.html](http://www.eecis.udel.edu/~ntp/ntp_spool/html/index.html)

There are very few changes that are needed to enable your server to be an NTP client and none to be an NTP server.  Once you have added server peers to supply a clock source to your system, other devices on your network can be pointed to your server and will take clock from it.  For example, this is an extract from my /etc/ntp.conf

server 0.us.pool.ntp.org
server 0.ca.pool.ntp.org
server 0.uk.pool.ntp.org
server 1.us.pool.ntp.org
server 1.ca.pool.ntp.org
server 1.uk.pool.ntp.org

This allows me to sync with up to 6 randomly selected stratum, 1, 2, or 3 servers, two of each in the US, Canada and the UK.  I have this many, and in this distribution to ensure I get six unique peers, and a good spread of quality.

I also have

server 127.127.1.0
fudge 127.127.1.0 stratum 10

This allows my server to use it's own clock as a clock source, but a much less desirable source.  In the event that my WAN link fails, it allows this server to continue to serve clock to the network, and to believe that it has a valid NTP source.

On my clients I simply have

server my_ntp_server.com

Beyond this you can add authentication, (do you care on your home network?) etc.

To confirm correct operation issue

ntpq -p

This will list the peers you have, and indicate which are your primary and secondaries, as well as their stratum levels - this also helps to understand why having multiple is servers configured is desirous.

Other useful commands are

ntptrace - to trace up the NTP stack, you may notice that you need to add interrogation capabilities to the server NTP config to make this really work from the clients - again I've not bothered as I can also ssh to the server.

ntpq has an interactive mode.  In that "as" lists the associated peers and how they are being used by you NTP server, and "rv" + the assID from the as list shows you considerable detail about each peer.

ntpdc -l will list the ntp sources as well (and your broadcasts), but not your clients.

ntpdc -p is very similar to ntpq -p

An area I have failed to get to work is using broadcast or multicast from my server.  My original plan was to sync my server and have it broadcast the clock to my LAN.  I was never able to get my server to broadcast/multicast the clock signal with a stratum level of less than 16.  If anyone has cracked that, I'd love to know...

I have assumed the concept of stratum is understood, if not, and to my crude understanding

Stratum 1 is a primary source with considerable accuracy, such as  from a caesium clock, or GPS etc.
Stratum 2 is basically a client of a Stratum 1 clock
Stratum 3 is a client of a Stratum 2 etc.
Stratum 16 is the lowest level - you cannot use a stratum 16 clock as a clock source.

For nearly every requirement, being a stratum 3 or 4 device is more than precise enough.  Personally I care to the 10s of seconds accuracy, and stratum 4 is considerably more accurate than that.  For this reason, and the desire to be a reasonable Internet citizen, I only have one device taking clock signals from outside my LAN.

I hope this helps - NTP is far easier to use than it initially appears, and while it is an incredibly complex piece of software, the reality is it simply doesn't matter to most of us as the configuration can be quite simple.

Alan

---

