---
title: "fail2ban not working"
date: 2007-10-05
forum: Server Platforms
---

### Post by wodka on 2007-10-05
My fail2ban isn't working. I'm using 6.06 LTS and fail2ban 0.6.0-3 or whatever version in the repository for dapper. 

Problems i've encountered so far:

At first, fail2ban would ban IP of person making multiple attempts in iptables, but the person making attempts was still able to keep trying.. as in it didn't ban the person at all.

I fixed that by changing the DROP to REJECT and editing the failregex to this:

[http://wiki.kartbuilding.net/index.php/Iptables_Firewall#Problems_with_fail2ban_and_ssh_attempts_on_ubuntu](http://wiki.kartbuilding.net/index.php/Iptables_Firewall#Problems_with_fail2ban_and_ssh_attempts_on_ubuntu)

It now successfully bans people making attempts on users who do not exist. It does not ban for multiple password tries on say root or other real usernames.

What's wrong now? and why did the original settings not ban/DROP anyone? 

English isn't my first language but I did the best I could! Thanks.

---

### Post by HermanAB on 2007-10-05
I recommend against using kludges like fail2ban.  Rather  use iptables rate limiting.  Rate limiting protects against every kind of DOS attack, including pings, slashdottings and brute forcings.  This is preferable, since it won't lock out legit user accidentally and helps against a wide range of attacks.

Cheers,

Herman

---

### Post by wodka on 2007-10-05
where could I read up about that? I'm pretty new to ubuntu/linux.

---

### Post by HermanAB on 2007-10-05
That's easy:
[http://www.google.ca/search?q=iptables+rate+limiting](http://www.google.ca/search?q=iptables+rate+limiting)
:)

---

### Post by wodka on 2007-10-05
Fail2ban is much easier. :] I like the auto unban. So, is there no way to fix my fail2ban?

Also, I am using an old version.. is it possible to install the newer one or will it not work with 6.06 LTS?

---

### Post by MJN on 2007-10-06
Post your fail2ban config, relevent auth.log snippets (showing the attempts) and the fail2ban log then we can take a look to see what's wrong.

Mathew

---

### Post by HermanAB on 2007-10-06
"Fail2ban is easier":

Not quite.  You only need to add *one* line to a start-up script:
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 1/minute --limit-burst 5 -j ACCEPT

Put that single long line at the end of /etc/rc.local and your machine will be effectively protected against any and all DOS attacks.  It is really hard to make something simpler than a one liner.

What it does, is to allow only one new connection attempt for any service at an average rate of 1 per minute.  This makes any abuse quite impossible.  However, it allows a burst of 5 per minute initially, which makes it unnoticeable to normal users.  If the normal load of your machine is higher, then turn those numbers up a bit.

Programs like fail2ban are unfortunate kludges that are best avoided, since they have serious downsides and can be used to DOS you, by locking you and all your users out, by using simple IP address spoofing techniques for example.

Cheers,

Herman

---

### Post by MJN on 2007-10-07
I like that one-liner - it certainly does look nice and simple.

I'm currently using Fail2ban and it works fine for me but I might give that line a go. Are there any drawbacks that you can think of? You mentioned the risk of being DOS'd by IP spoofing - is this rule not subject to the same risk?

Mathew

---

### Post by HermanAB on 2007-10-07
Yes, one could hammer a server causing it to rate limit, but it will still allow connections for everybody, so after a while you should be able to connect.  Whereas, if Fail2ban black listed your IP address, then you are screwed.  This is rather important if your server is in a data centre on the other side of the planet and you can't walk over there and plug in a terminal.

Note that the rate limiter only limits *new* connections.  As soon as a connection is established, it can run at full speed.  It does not do bandwidth limiting.  With a typical brute force attack, each try is a new connection.  Of course there are always exceptions to that: The Microsoft SMB protocol allows one to embed thousands of queries in a single packet, but anyone who tries to use SMB over a WAN deserves to get shot down!

Anyhoo, rate limiting is effective against a multitude of things like 'ping of death', SSH and FTP brute forcers, Slashdottings and even email spam floods.  It is very effective against most kinds of server abuse.  It allows you to determine what is a reasonable operating range and enforce it, such that normal traffic is not impeded, but as soon as some limit is exceeded, it just shakes off the abuse and most abusers will then give up and go away.

Cheers,

Herman

---

### Post by MJN on 2007-10-07
Thanks for the explanation.

I think the one-liner is perhaps a little too brutal for my liking - I've had a look round and found a few combos (2/3 lines) to concentrate on just SSH traffic so I might read up some more on the subject before deciding on what to settle on.

Thanks again,

Mathew

P.S. You mentioned permanent lockouts, with Fail2ban there is no risk of this happening - the lockout time is adjustable.

---

### Post by HermanAB on 2007-10-07
Oh, just toss a --dport 22 statement in there if you wish it to be only effective for SSH.  On my servers, I do bandwidth limiting, which is more complex, but I do think that a simple rule like the above will be just as effective.

---

### Post by MJN on 2007-10-07
The more I read about using iptables alone to do this the more I am wondering why anyone is using Fail2ban and many other similar-tools. Indeed why were they written, given that most ultimately use iptables as the backend block tool? Or are these iptables directive (limit-burst etc) more recent additions?

Come on HermanAB, what are the downsides to this technique as it's sounding too good to be true (compared with having a Fail2ban daemon running, and operating in a reactive way on the logs as opposed to realtime). :)

Mathew

---

### Post by HermanAB on 2007-10-07
Why use other tools -  Have you ever tried to read the iptables man page?
:)

I think that the main reason is the obscurity of iptables in general. Rusty Russel has done an amazing job with iptables, but easy it sure ain't, especially the first 10 times or so.

The rate limiting and tarpit modules are 'recent' additions, but recent as in the last five years isn't exactly recent anymore.

There are no serious downsides - rate limiting was specifically designed to handle the problem of server abuse and it does that very well.

For fun, you should also look at the iptables tarpit modules.  If you have an extra server lying around (any old POS will do), then you can set it up to keep connections to abusers open and bog their machines down - pure evil genius...

Cheers,

H.

---

