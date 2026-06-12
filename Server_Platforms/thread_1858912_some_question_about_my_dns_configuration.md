---
title: "some question about my dns configuration"
date: 2011-10-13
forum: Server Platforms
---

### Post by mrm-mm on 2011-10-13
hi guys
i have ubuntu server bind9 dns with this hardware
system dell 780 , cpu c2d , ram 2 G
and iam working in internet service providing company, there is a problem with the web browsing some time become slow, my boss tell me the cause of this problem is from our dns bind9 server so i want to now is my dns configuration slow the network performance ?
and how can i check the performance of the dns server ? the configuration of the bind9 is

in named.conf.options the forwarder is activated
forwarder
{
8.8.8.8;
x,x,x,x;
}

in named.conf.local there are two zone definition
zone "example.com" {
type master;
file = "/etc/bind/zones/db.example.com";
}

and the reverse zone is
zone "50.50.92.in-addr.arpa" {
type master;
notify no;
file "/etc/bind/zones/db.92";
}

now the zones files is
db.example.com file
$TTL    604800
@    IN    SOA    ns1.example.com. root.example.com. (
             2011090400        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns1.example.com.
ns1     IN      A       92.50.50.190
www   IN      A       92.50.50.195
host    IN     A        92.50.50.200

db.92
$TTL    604800
@    IN    SOA    ns1.example.com. root.example.iq. (
             2011090403        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns1.
1.0.0   IN      PTR     localhost.
190     IN      PTR     ns1.example.com.
195     IN      PTR     [www.example.com]("http://www.example.com").
200     IN      PTR     host.example.com.

this the end of configuration file
the dns ip : 92.50.50.190
the resolv file contain only the dns ip 92.50.50.190
is there any wrong in my configuration ?
does the dns in this configuration do any cache process ?
if i activate the recursion options in options configuration file, is this usefull for me ?
does my dns server takes it's query from the root server or its taking query only from forwarders ip ?
is there any tools to check my dns performance or to check the traffic on my dns interfaces ?
sorry for so many question iam new in ubuntu and servers please help me
thanks

---

### Post by Jonathan L on 2011-10-13
> **mrm-mm said:**
> hi guys
i have ubuntu server bind9 dns with this hardware
system dell 780 , cpu c2d , ram 2 G
and iam working in internet service providing company, there is a problem with the web browsing some time become slow, my boss tell me the cause of this problem is from our dns bind9 server so i want to now is my dns configuration slow the network performance ?
and how can i check the performance of the dns server ? the configuration of the bind9 is
[...]

this the end of configuration file
the dns ip : 92.50.50.190
the resolv file contain only the dns ip 92.50.50.190
is there any wrong in my configuration ?
does the dns in this configuration do any cache process ?
if i activate the recursion options in options configuration file, is this usefull for me ?
does my dns server takes it's query from the root server or its taking query only from forwarders ip ?
is there any tools to check my dns performance or to check the traffic on my dns interfaces ?
sorry for so many question iam new in ubuntu and servers please help me
thanks

Hi M

DNS can be a tricky subject as there's a lot of subtlety to it.

The firrst thing is separate in your mind the following functions:

1.  EXTERNAL RESOLUTION.  Resolving names to addresses when your computers ask questions about other computers (ie, when one of your computers browses to [www.ubuntu.com]("http://www.ubuntu.com") and wants the answer 91.189.90.40).

2.  HOSTING YOUR DOMAIN'S DNS. Definining names to addresses when other computers ask questions about your computers (ie, when someone else browses to [www.yourdomain.com]("http://www.yourdomain.com") and wants the aanswer 92.50.50.195)

3.  INTERNAL RESOLUTION. Resolving names to addresses when your computers ask about your own computers (ie, internal browsing to [www.yourdomain.com]("http://www.yourdomain.com") and wants the answer 10.0.0.195 or whatever you're using)  This only really happens when you've got a sizeable number of inside machines, ie in a business.

4.  CLIENT RESOLUTION SERVICES.  DNS resolution functions for your clients asking about public computers (ie, when one of your clients computers browses to [www.ubuntu.com]("http://www.ubuntu.com") and wants the answer 91.189.90.40).  This is only really done at an ISP or a web hosting computer.

Measuring

It's good to measure things when people say the web is slow.  A simple way to find this out is to time some wgets to a known place, perhaps by cron every 10 minutes, ideally for a 1kbyte and a 1Mbyte file.  Do wgets to that place by name and by IP address.  Is anything taking a very long time (90s or 120s?) because that's often just a signal that there is some DNS timing out.

You can time DNS lookups directly with dig.

Caching

The general rule about DNS is that you can presume everything caches everything everywhere.


Hope that helps clarify a little bit.  Now ... which functions are you saying have the problems?

Kind regards,
Jonathan.

---

### Post by mrm-mm on 2011-10-14
dear jonathan thank you for your reply
> which functions are you saying have the problems?

my problem is the slow in web browsing iam using dns as 
> 3.  INTERNAL RESOLUTION. Resolving names to addresses when your  computers ask about your own computers (ie, internal browsing to [www.yourdomain.com]("http://www.yourdomain.com/")  and wants the answer 10.0.0.195 or whatever you're using)  This only  really happens when you've got a sizeable number of inside machines, ie  in a business
i think this type that fit my needs i have limit number of A records, i work in internet providing company not in web hosting company, beside the resolving of a few records (approximately 5 records that does not increase in the future ) i want my dns to work as a cache dns server, so i activate the forwarder options thinking that will cache the query in the server ram.
> Measuring

It's good to measure things when people say the web is slow.  A simple  way to find this out is to time some wgets to a known place, perhaps by  cron every 10 minutes, ideally for a 1kbyte and a 1Mbyte file.  Do wgets  to that place by name and by IP address.  Is anything taking a very  long time (90s or 120s?) because that's often just a signal that there  is some DNS timing out.
sorry this section i don't understand it can you explain it for me please ?
iam not a professional 
sorry for my bad English and thank you very much 

best regards
mustafa

---

### Post by Jonathan L on 2011-10-16
> **mrm-mm said:**
> dear jonathan thank you for your reply

my problem is the slow in web browsing iam using dns as 

i think this type that fit my needs i have limit number of A records, i work in internet providing company not in web hosting company, beside the resolving of a few records (approximately 5 records that does not increase in the future ) i want my dns to work as a cache dns server, so i activate the forwarder options thinking that will cache the query in the server ram.

sorry this section i don't understand it can you explain it for me please ?
iam not a professional 
sorry for my bad English and thank you very much 

best regards
mustafa

Hi Mustafa

Switching forwarding on sounds right to me, given what you're saying you're doing.  I have to confess I am not clear what problem you're trying to solve, so what I'm saying below is completely general.  I'd have guessed you have also got external resolution, if someone is complaining about web speeds.

Sorry if I was unclear about measuring.  If someone says "web is slow", I think it's a good idea to measure it.  So my suggestion is to find, somewhere on the web, a small file and a larger one on the same server at a large host, such as these two at Wikipedia:

(These links look the same but are not)

[LIST]
[*][http://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Olhos_de_um_gato-3.jpg/50px-Olhos_de_um_gato-3.jpg](http://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Olhos_de_um_gato-3.jpg/50px-Olhos_de_um_gato-3.jpg)
[*][http://upload.wikimedia.org/wikipedia/commons/b/bf/Olhos_de_um_gato-3.jpg](http://upload.wikimedia.org/wikipedia/commons/b/bf/Olhos_de_um_gato-3.jpg)
[/LIST]

You can then get them with wget which will give you timings, like this:
```
wget -o /tmp/LOG -O /dev/null http://upload.wikimedia.org/wikipedia/commons/b/bf/Olhos_de_um_gato-3.jpg
```You'll see the useful summary line at the bottom
```
2011-10-16 14:08:38 (251 KB/s) - `/dev/null' saved [4909/4909]
```If you have timings taken frequently you'll easily see any patterns, such as different speeds at different times of day.  You change change the number of pixels ("50px" in example above) to get different sized thumbnails from Wikipedia which is very handy.  Attached a graph of my speeds on a domestic ADSL line in London which I did today.  You'll see it takes about 20 ms to do the DNS and get any connection.  The trend line shows it as 16 ms + 1.5 ms / kbyte of file.

Also time your DNS: dig gives good output
```
dig www.wikipedia.org
;; Query time: 25 msec

```Hope that's of some use.

My comment about very long timings: if you have anything which takes, repeatably, exactly 30, 60, 90, or 120 seconds, then usually you have something which is failing and then timing out.  This would be indicative of trying to use a non-existent DNS server, for example.

Just to repeat: I don't know what you're trying to solve, so I'm just giving you general tips for addressing DNS and web timings.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2011-10-17
I'd actually suggest the opposite -- try turning off forwarding.  By default the DNS server queries the root domains for names and caches the results locally. By using a forwarder, you're not letting the local server build its cache.

---

### Post by Jonathan L on 2011-10-17
> **SeijiSensei said:**
> I'd actually suggest the opposite -- try turning off forwarding.  By default the DNS server queries the root domains for names and caches the results locally. By using a forwarder, you're not letting the local server build its cache.

... I agree with Sensei and disagree with myself!  It does all depend on what problem we're solving though.

Kind regards
Jonathan.

---

