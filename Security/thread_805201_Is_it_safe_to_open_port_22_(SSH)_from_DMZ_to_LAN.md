---
title: "Is it safe to open port 22 (SSH) from DMZ to LAN"
date: 2008-05-23
forum: Security
---

### Post by wjrhee77 on 2008-05-23
Hello, 

I have a server on DMZ port that uses rsync over ssh to backup files onto a backup server on LAN.

By default, firewall DENYS any port/services from DMZ to LAN.  So I ALLOWED SSH (port 22).  

Is this safe?  Thanks.

---

### Post by The Cog on 2008-05-24
Not entirely. If someone gets control of the machine on the DMZ, they then have a hole to get into your main LAN via whatever machine the DMZ machine uses SSH to.

Sometimes I think these things can't be avoided though.

---

### Post by yaztromo on 2008-05-24
At least follow some general precautions on opening up SSH

- Change the port to something other than 22
- Deny root access
- Only allow specified user name(s) access.

---

### Post by brian_p on 2008-05-24
> **wjrhee77 said:**
> Hello, 

I have a server on DMZ port that uses rsync over ssh to backup files onto a backup server on LAN.

By default, firewall DENYS any port/services from DMZ to LAN.  So I ALLOWED SSH (port 22).  

Is this safe?  Thanks.

The server software is up to date and configured securely? That will reduce unauthorized access to so close to zero as not to matter.

rsync over ssh is secured; for example, by restricting authorized_keys so that sshd on the LAN host will only accept a connection from rsync?

Looks safe to me.

---

### Post by wjrhee77 on 2008-05-27
Great!  Thanks for all your inputs.

---

### Post by hyper_ch on 2008-05-28
changing ports won't do much good

use a tool like denyhosts that will auto-ban an ip after several failed login attemps

use strong passwords

maybe create another user and give him root rights (if you require root to rsync the files) and use this one then for rsyncing

---

### Post by rickyjones on 2008-05-28
> **hyper_ch said:**
> changing ports won't do much good

use a tool like denyhosts that will auto-ban an ip after several failed login attemps

use strong passwords

maybe create another user and give him root rights (if you require root to rsync the files) and use this one then for rsyncing

I disagree with the first part - changing ports WILL do a lot of good. I would have several hundred attempts in a 48 hour period when using port 22. After switching to port 22222 it dropped to 0.

Beyond that, yes, using strong passwords and denyhosts will also go a long way (much longer than changing ports).

-Richard

---

### Post by hyper_ch on 2008-05-28
if those several hundred attempts just check port 22 then you don't have to worry about them anyway ;)

---

### Post by rickyjones on 2008-05-28
> **hyper_ch said:**
> if those several hundred attempts just check port 22 then you don't have to worry about them anyway ;)

By "attempts" I mean someone tried to log onto the server. Naturally these are bot programs looking for any open SSH server. Moving the port to something else will render them rather useless as they usually only look at the default port.

-Richard

---

### Post by hyper_ch on 2008-05-28
I know what you mean.... and hence my answer ;)

---

### Post by yaztromo on 2008-05-28
> **hyper_ch said:**
> if those several hundred attempts just check port 22 then you don't have to worry about them anyway ;)

You should be concerned about all unauthorized attempts to access your SSH server, be it by bot or human. Unless there is some pressing reason to stay with 22 you should always change the default port.

---

### Post by hyper_ch on 2008-05-28
why should I be concerend about script kiddies? denyhosts takes care of that...

Those that one really need to be worried about are those, that try also the other ports... and for them changing ports will not change anything... except that quite a few thing that relay somehow on SSH will have a lot more troubles (e.g. rsyncing over ssh) ;)

---

### Post by yaztromo on 2008-05-28
Denyhosts isn't everything, nothing wrong with using both. 

Even the denyhosts FAQ suggests to change the port, it is just good practice.

And for the record I've never had any problems with changing the SSH port, including with rsync.

---

### Post by hyper_ch on 2008-05-29
I know denyhosts isn't everything... it stops the script kiddies... and it may help against serious hackers... however changing ports will not help against serious hackers - you'll just make feel yourself safer why no additional security is added.

---

### Post by yaztromo on 2008-05-29
Yet additional security is added. If a new flaw is found in SSH before it is patched, my server is lot safer (through obscurity) from bots checking port 22 that know about the new flaw, denyhosts only really prevents agaisnt brute forcing, which is not good enough for serious use.

You have to remember that additional security is added on every little precaution you take.

---

### Post by hyper_ch on 2008-05-29
you think that by changing port additional security will be added... this is not the case.

---

### Post by rickyjones on 2008-05-29
> **hyper_ch said:**
> you think that by changing port additional security will be added... this is not the case.

I disagree.

Take a standard cylinder of some sort. Put it out in the rain. If you have a hole in the top then the rain, as it continually pounds against it, will more easily get in. But if you put a hole in the bottom instead then the rain will have a harder time getting in. It is still possible but it will take longer and will require even more rain.

The cylinder is your computer. Moving the hole (port) will not make you 100% secure, but it will add to your security by making the entrance so much more difficult to find.

Sincerely,
Richard

---

### Post by hyper_ch on 2008-05-29
you have the hole anyway... so your analogy fails ;)

---

### Post by rickyjones on 2008-05-29
> **hyper_ch said:**
> you have the hole anyway... so your analogy fails ;)

Going by the logic of this last sentence it sounds like the only good solution is to close the hole. I agree, closing the hole would make your server MUCH more secure, but the whole point is to have the hole open in a way that can make the server as safe and secure as possible.

Coupling a different port # along with denyhosts (notice how I've never disagreed with using a third party security tool to help secure OpenSSH) WILL cut down on intrusion attempts.

The less intrusion attempts you have the less likely you are to have a break in.

Because, you know, all it takes is for that bot program to guess the right username/password combination ONCE to get past that fancy third party tool. BUT, if the bot program is looking on port 22 and you are listening on 22222 then it doesn't matter HOW many times it tries, it will NOT get in.

Will this completely stop a true professional? No, but that is why you have the third party tool (DenyHosts), to stop that.

No matter what you do, if a true professional manages to guess the right username/password combo, and the right port, they still get access to your files. 

Every little bit help. Once again, moving the port will not make you 100% secure, but it will ADD to it. Value added protection by changing one simple item.

Sincerely,
Richard

---

### Post by brian_p on 2008-05-29
> **rickyjones said:**
> Every little bit help. Once again, moving the port will not make you 100% secure, but it will ADD to it. Value added protection by changing one simple item.

I don't really care what non-standard ports people choose to run services on but claiming it adds any security whatsoever is incorrect. Doing it because it eliminates scripted probes is a personal choice and on those grounds I'd go along with it, even though I think it is silly. Promoting it as a security measure is a different matter.

The security of ssh rests on strong passwords or rsa/dsa keys. Anyone using weak passwords hasn't any useful input to make to this topic.

Now, how long would it take to brute force an rsa key? Let's be conservative and say 1,000,000 years. And how long to discover which port sshd is listening on. A really inept scan might take a week. Not exactly value added protection and sufficient to indicate how little changing ports adds to security.

---

### Post by rickyjones on 2008-05-29
> **brian_p said:**
> I don't really care what non-standard ports people choose to run services on but claiming it adds any security whatsoever is incorrect. Doing it because it eliminates scripted probes is a personal choice and on those grounds I'd go along with it, even though I think it is silly. Promoting it as a security measure is a different matter.

The security of ssh rests on strong passwords or rsa/dsa keys. Anyone using weak passwords hasn't any useful input to make to this topic.

Now, how long would it take to brute force an rsa key? Let's be conservative and say 1,000,000 years. And how long to discover which port sshd is listening on. A really inept scan might take a week. Not exactly value added protection and sufficient to indicate how little changing ports adds to security.

Since the majority of intrusion attempts appear, from my experience, to be from bots only scanning port 22, I believe that it does in fact raise security by changing the port.

I'm not going to try to beat anyone up to enforce my beliefs, I'm just sharing my experiences and letting others make their own decisions. If you enjoy having your logs filled with invalid login attempts due to repeated attacks from using the default port then go right ahead and do it. I'll continue using a non-standard port where most attackers usually don't think to look.

As I stated, this does not replace strong passwords or the use of other tools to ensure the integrity of your system. However every little bit helps. By the same logic why would the inclusion of DenyHosts be seen as a good defensive security measure? After all, if the only thing that counts is using a strong password and/or an RSA key based login then why have DenyHosts, or another third party utility?

Sincerely,
Richard

---

### Post by brian_p on 2008-05-29
> **yaztromo said:**
> Yet additional security is added. If a new flaw is found in SSH before it is patched, my server is lot safer (through obscurity) from bots checking port 22 that know about the new flaw, denyhosts only really prevents agaisnt brute forcing, which is not good enough for serious use.

But it is not safe from bots that know about the new flaw and which scan all ports. Or do you think the people who devise these things are not resourceful enough to think of doing that? 

> You have to remember that additional security is added on every little precaution you take.

Not necessarily. Looking both ways as you cross a road will get you a long way in life. Waiting for the highway to be clear for 10 km in both directions before venturing off the pavement adds little to your safety.

---

### Post by rickyjones on 2008-05-29
> **brian_p said:**
> 
Not necessarily. Looking both ways as you cross a road will get you a long way in life. Waiting for the highway to be clear for 10 km in both directions before venturing off the pavement adds little to your safety.

Let me try a different example, because in your analogy both items appear to give you additional safety, which is kind of my point. Waiting for the highway to be clear for 10 km in both directions may be slightly overkill but it does make you safe, correct?

Take two soldiers. One soldier has body armor, the other does not. The solder with the body armor is in a valley with 10 enemy soldiers who are firing on him with submachine guns in broad daylight. The other soldier, wearing no armor, is sneaking around the top of the basis, through the woods, at night, while the majority of enemy soldiers are sleeping or are still busy in the valley.

Which soldier is most likely to survive the longest?

Sincerely,
Richard

---

### Post by brian_p on 2008-05-29
> **rickyjones said:**
> Since the majority of intrusion attempts appear, from my experience, to be from bots only scanning port 22, I believe that it does in fact raise security by changing the port.

You've completely ignored the argument I made showing there is no security enhancement. There is also the point that automatic scripts are braindead. The chances of one of them getting a valid username on a machine are so remote as to be zero. That's before they even get round to passwords.

> I'm not going to try to beat anyone up to enforce my beliefs, I'm just sharing my experiences and letting others make their own decisions. If you enjoy having your logs filled with invalid login attempts due to repeated attacks from using the default port then go right ahead and do it. I'll continue using a non-standard port where most attackers usually don't think to look.

That's ok, but has nothing to do with the security of the service.

> As I stated, this does not replace strong passwords or the use of other tools to ensure the integrity of your system. However every little bit helps. By the same logic why would the inclusion of DenyHosts be seen as a good defensive security measure? After all, if the only thing that counts is using a strong password and/or an RSA key based login then why have DenyHosts, or another third party utility?

Why use them indeed? They also add no security.

---

### Post by rickyjones on 2008-05-29
> **brian_p said:**
> You've completely ignored the argument I made showing there is no security enhancement. There is also the point that automatic scripts are braindead. The chances of one of them getting a valid username on a machine are so remote as to be zero. That's before they even get round to passwords.

I disagree. Why give them a chance to attempt to enter a username/password combination? By removing that ability (changing the port) you inherently increase the security. If a program cannot automatically attempt an intrusion you just increased security. It is OK, feel free to admit it. :P

> **brian_p said:**
> 
That's ok, but has nothing to do with the security of the service.

Again, I disagree. Making sure that your log files are not filled with erroneous entries is very much a part of the server security as a whole. For example, if you leave your log files alone and they overflow then you could run into issues on the server due to a lack of disk space. If your server goes down due to a large log file who will be blamed?

> **brian_p said:**
> 
Why use them indeed? They also add no security.
Well they do add some security. As I said, every little bit helps. This is why we have perimeter firewalls. This is why you mandate strong passwords. This is why you switch default ports. You should do everything that is reasonable to ensure the security of your system. Even if it only deflects 10% of the intrusion attempts it is still worth doing it. It is all about your risk assessment, and cost versus benefits analysis. If it takes all of five minutes to change the port assignment, and it saves the company $100 in possible recovery costs later down the road (or management costs to trim log files) then it well worth the initial cost of five minutes.

Great debate by the way, I'm enjoying this.

For my own personal curiosity, however, may I ask how you go about securing your servers? As you shoot down my ideas as not being worth it I'm curious about your own security practices. If you don't wish the world to see them then I wouldn't mind discussing them more via PM.

Sincerely,
Richard

---

### Post by brian_p on 2008-05-29
> **rickyjones said:**
> Let me try a different example, because in your analogy both items appear to give you additional safety, which is kind of my point. Waiting for the highway to be clear for 10 km in both directions may be slightly overkill but it does make you safe, correct?

Take two soldiers. One soldier has body armor, the other does not. The solder with the body armor is in a valley with 10 enemy soldiers who are firing on him with submachine guns in broad daylight. The other soldier, wearing no armor, is sneaking around the top of the basis, through the woods, at night, while the majority of enemy soldiers are sleeping or are still busy in the valley.

Which soldier is most likely to survive the longest?

I always end up regretting it when I get involved in analogies! I would say yours would have to have both soldiers wearing impregnable body armour to examine the 'every little bit aids security' argument.

---

### Post by rickyjones on 2008-05-29
> **brian_p said:**
> I always end up regretting it when I get involved in analogies! I would say yours would have to have both soldiers wearing impregnable body armour to examine the 'every little bit aids security' argument.

I wouldn't say that they need impenetrable body armor for the analogy to work. We are looking at which situation is a safer situation to be in.

Out in the open with 10 rifles aimed at you? Or crawling through a field in the middle of the night with the majority of your enemies busy somewhere else?

In this analogy the solder is the server. The soldier with the body armor has a very strong password. However he is under constant attack. It will only be a matter of time, because he is out in the open, before one of those rifles finishes him off.

The other soldier is craftier. He avoids the battle below and is undetected. Could someone still find him up at the top of the valley? Yes. However he will most likely last much longer than the soldier in the valley.

Likewise an open door under constant attack is worse off then an open door that only gets attacked once or twice in the same time period.

Security isn't just about using strong passwords to keep people out. It is also about minimizing those risks. If 90% of your attacks are on a certain port, then close that port and use a different one. Instantly you remove the incentive to look at the port. You also save bandwidth.

Sincerely,
Richard

---

### Post by brian_p on 2008-05-29
> **rickyjones said:**
> I disagree. Why give them a chance to attempt to enter a username/password combination? By removing that ability (changing the port) you inherently increase the security. If a program cannot automatically attempt an intrusion you just increased security. It is OK, feel free to admit it. :P

Could we up the ante? 100,000,000 years to crack a 2048 rsa key. 1 hour to do a competent port scan. Altering the default port gives no increase in the security of sshd.


> Again, I disagree. Making sure that your log files are not filled with erroneous entries is very much a part of the server security as a whole. For example, if you leave your log files alone and they overflow then you could run into issues on the server due to a lack of disk space. If your server goes down due to a large log file who will be blamed?

I did specify security 'of the service'. You've widened it to /var filling up. Yes, it's a possible issue so it's not unreasonable to take steps to minimise it happening. 

> For my own personal curiosity, however, may I ask how you go about securing your servers? As you shoot down my ideas as not being worth it I'm curious about your own security practices. If you don't wish the world to see them then I wouldn't mind discussing them more via PM.

You'll be disappointed! The network is small. 3 Linux boxes, none firewalled. Sshd is on port 22 with public key authentication and 'PermitRootLogin no', which I think are the only default settings I've changed. There are 3 other devices which have ports 23 and 80 firewalled, but that's because they have proprietary firmware whose security status is not completely known to me and also it is doubtful it will ever be updated.

---

### Post by rickyjones on 2008-05-29
> **brian_p said:**
> Could we up the ante? 100,000,000 years to crack a 2048 rsa key. 1 hour to do a competent port scan. Altering the default port gives no increase in the security of sshd.

I get the feeling that you are ignoring the fact that I'm also recommending strong passwords here. No matter how strong your key, if someone does guess the correct key and is ONLY looking at port 22 then you would be better off using a non-standard port to throw people off. Altering the port WITHOUT using strong password security DOES increase security, albeit it is still only as strong as your password. Hence why I am advocating port changes AND strong passwords.

> **brian_p said:**
> 
I did specify security 'of the service'. You've widened it to /var filling up. Yes, it's a possible issue so it's not unreasonable to take steps to minimise it happening. 

The security of the service affects the welfare of the entire server.

> **brian_p said:**
> 
You'll be disappointed! The network is small. 3 Linux boxes, none firewalled. Sshd is on port 22 with public key authentication and 'PermitRootLogin no', which I think are the only default settings I've changed. There are 3 other devices which have ports 23 and 80 firewalled, but that's because they have proprietary firmware whose security status is not completely known to me and also it is doubtful it will ever be updated.
I still feel as though you'd be slightly better off changing your ports. However to each his own.

Security is only as strong as your weakest link. Every single part of your security plan should work in tandem. I feel that this includes strong passwords and/or using public keys. In addition changing the ports to throw off common script attacks is highly effective. To claim that it is not is to ignore basic statistics.

If port 22 is scanned and attacked 100 times per hour then you have a two issues: more people trying to attack means more chances for success; more people trying to get in ties up your bandwidth slowing down critical functions (like when you try to connect to your SSH server. If it is too busy dealing with unauthorized requests then this impacts your productivity).

However if port 22222 is only scanned and attacked once per hour then you reduced your risk by almost 100%. Less attempts against your server will result in the use of less bandwidth, along with leaving your service open to accept your login attempts. This will maintain your productivity levels.

Theoretically the more we talk about this the more we may end up disagreeing. However here is something that you might agree with. Probably one of the best ways to secure your server that has OpenSSH access would be to set it up so that only authorized IP addresses are allowed to even attempt a connection. That, or else configure your server to only be accessed via VPN tunnel.

Sincerely,
Richard

---

### Post by wootah on 2008-05-29
As a side note, fail2ban is a great script for controlling ssh access. If you hammer a server, that IP gets banned. There are a bunch of other features too. Take a look! :D

---

### Post by kevdog on 2008-05-29
How about adding a portknocker that would dynamically expose port 22 when the correct combination is sent by the client, and then later close the port to incoming connections?

Just an idea?:)
[http://www.portknocking.org/](http://www.portknocking.org/)

---

### Post by brian_p on 2008-05-30
> **rickyjones said:**
> I get the feeling that you are ignoring the fact that I'm also recommending strong passwords here.

On the contrary, my argument relies on your using strong passwords. What's the maths? 62 alphanumeric characters; a 12 character password; so something like 62^12 combinations at the very least to check. Then estimate how long that will take.

> No matter how strong your key, if someone does guess the correct key and is ONLY looking at port 22 then you would be better off using a non-standard port to throw people off.

There is more chance of winning top prize in a national lottery five weeks on the run than guessing a strong password or rsa key.

> Altering the port WITHOUT using strong password security DOES increase security, albeit it is still only as strong as your password.

It does but, as I've remarked earlier, people who use weak passwords have no contribution to make here.

> Hence why I am advocating port changes AND strong passwords.

Strong passwords are sufficient.

> If port 22 is scanned and attacked 100 times per hour then you have a two issues: more people trying to attack means more chances for success;

Let them try. Their chance of success is effectively zero. Please see above.

> more people trying to get in ties up your bandwidth slowing down critical functions (like when you try to connect to your SSH server. If it is too busy dealing with unauthorized requests then this impacts your productivity).

However if port 22222 is only scanned and attacked once per hour then you reduced your risk by almost 100%. Less attempts against your server will result in the use of less bandwidth, along with leaving your service open to accept your login attempts. This will maintain your productivity levels.

From my limited experience the impact of ssh probes on bandwidth or service availability is vastly overrated. Maybe it is different in the corporate world. I'd hazard a guess that the impact of spam is many orders of magnitude greater in respect of bandwidth etc.

Those who advise that you should or must move port seem to subscribe to the view that the internet is unsafe when with normal precautions it is not. Blacklist the offending IPs or move port by all means but sshd is secure on port 22.

> Theoretically the more we talk about this the more we may end up disagreeing. However here is something that you might agree with. Probably one of the best ways to secure your server that has OpenSSH access would be to set it up so that only authorized IP addresses are allowed to even attempt a connection. That, or else configure your server to only be accessed via VPN tunnel.

You're probably right but it is an interesting discussion. What is also interesting is that the originator of this thread, wrjhee77, isn't offering a ssh service open to the outside but was still advised to move it to a different port.

Once upon a time I did restrict IPs which were allowed to connect here. Then one day I happened to be in Madrid. And guess what I had forgotten to do? So never again. sshd is designed to be securely accessible from anywhere so that's the way I use it now.

---

### Post by wootah on 2008-05-30
> **kevdog said:**
> How about adding a portknocker that would dynamically expose port 22 when the correct combination is sent by the client, and then later close the port to incoming connections?

Just an idea?:)
[http://www.portknocking.org/](http://www.portknocking.org/)

Very interesting idea! I wonder if a man in the middle attack could compromise the knock-order?

---

### Post by Monicker on 2008-05-30
> **brian_p said:**
> 

From my limited experience the impact of ssh probes on bandwidth or service availability is vastly overrated. Maybe it is different in the corporate world. I'd hazard a guess that the impact of spam is many orders of magnitude greater in respect of bandwidth etc.


I have to agree with the above.  From what I have seen in our firewall logs, and from past traffic analysis, there is negligible impact from refused ssh connections.  I have definitely never seen enough to overwhelm a server and make it unusable.  Its not like you have to transfer much data to refuse an invalid connection attempt.  They don't even rise above the background noise from probes to other ports.

Attachments from a few spam messages in a single day will utilize far more bandwidth than all the ssh connection attempts for that same time period.

---

### Post by kevdog on 2008-05-30
> **wootah said:**
> Very interesting idea! I wonder if a man in the middle attack could compromise the knock-order?

MIM attack -- Im not an expert but I don't think this would work.

Let me make sure we are both on the same page.  And I am going to be speaking specifically of fwknop -- which is one instance of a port knocking program.  For other less sophisticated clients, yes Im sure a MIM attack could be possible.

fwknop - [http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)

The client sends an encrypted port knocking request.  Inside the port knock is the original senders IP address, a hash that would guarantee authenticity of the port knock if it were somehow decoded and changed.  In addition the port knock is encrypted -- and the MIM would need to know the password to decrypt the packet.  If the packet were simply sent along to the server, the MIM would not have access since the IP address of the firewall is only modified to allow access to the client's IP address.  The packet could also not be held and later replayed, since each packet has a unique random number to prevent packet replay.  An additional optional feature is that the packet could be gpg encrypted -- meaning its signed with the clients key and encrypted with the servers key.  Even if this packet were intercepted -- in this scenario with asymmetric encryption, I would believe it nearly impossible to decode the packet.

I've recently writen a How-To for setting up fwknop with Ubuntu:
[http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

---

### Post by dakal on 2008-05-31
> **kevdog said:**
> How about adding a portknocker that would dynamically expose port 22 when the correct combination is sent by the client, and then later close the port to incoming connections?

I'll admit, I haven't read the whole thread in detail, but the first question would be: what is the threat model? If you are worried about someone breaking into the DMZ host and being able to get through to the LAN over SSH by ordinary means, a strong password or other authentication measure by itself won't do much good, since rsync probably needs to run unattended. When someone has broken into a system, it is safest to assume that they have root access and thus can read/write any file on the system as well as inspect the contents of the system memory. So any protection would have to be on the server (LAN) side.

Set up the SSH server to only allow one specific login, which has the minimum required privileges required to carry out the task. Use for example public key authentication and set it up to only accept the passphrase-less key from the one IP of the DMZ host and to only allow execution of rsync when said key is used. Run the SSH server on a non-standard port if possible. Make sure both the SSH server and the rsync server are up to date at all times and properly configured. And do your best to secure the DMZ host (which should be done anyway).

---

### Post by hyper_ch on 2008-05-31
well, you initiate rsync from the backup server... you will not rsync into the backup server ;)

---

### Post by kevdog on 2008-05-31
dakal

Your method you propose is excellent.  However if you lock your iptables to be so restrictive, this could potentially run into problems if you using ssh to access the server from different networks or different IP addresses.

Again its a tradeoff between stringency and flexibility.  I'm not saying its the end-all-be-all, however port knocking allows use of a very restrictive firewall, but also allows for dynamic flexibility.  Depending on the setup of the port knocker, this level of flexibility can definitely be modified to one's need.

Again fail2ban is another option, as well as a using the recent iptables module to limit repeated connection attempts.  

There is no ideal solution, just the amount of flexibility you would like to introduce.

---

### Post by dakal on 2008-06-01
> **kevdog said:**
> dakal

Your method you propose is excellent.  However if you lock your iptables to be so restrictive, this could potentially run into problems if you using ssh to access the server from different networks or different IP addresses.

Yes, higher security generally means less convenience. It's always a tradeoff, whether it's a server host firewall or nuclear ICBM launch procedures.

However, when the usage scenario is very narrow, you can usually go with relatively tight security without it causing an inconvenience. It's not very likely that you are going to need to backup to/from a system with a different IP address without knowing in advance. A more likely scenario would be that you would need to restore the backup without knowing one of the IP addresses involved beforehand, but that would involve some planning anyway.

---

### Post by wootah on 2008-06-02
> **kevdog said:**
> MIM attack -- Im not an expert but I don't think this would work.

Let me make sure we are both on the same page.  And I am going to be speaking specifically of fwknop -- which is one instance of a port knocking program.  For other less sophisticated clients, yes Im sure a MIM attack could be possible.

fwknop - [http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)

The client sends an encrypted port knocking request.  Inside the port knock is the original senders IP address, a hash that would guarantee authenticity of the port knock if it were somehow decoded and changed.  In addition the port knock is encrypted -- and the MIM would need to know the password to decrypt the packet.  If the packet were simply sent along to the server, the MIM would not have access since the IP address of the firewall is only modified to allow access to the client's IP address.  The packet could also not be held and later replayed, since each packet has a unique random number to prevent packet replay.  An additional optional feature is that the packet could be gpg encrypted -- meaning its signed with the clients key and encrypted with the servers key.  Even if this packet were intercepted -- in this scenario with asymmetric encryption, I would believe it nearly impossible to decode the packet.

I've recently writen a How-To for setting up fwknop with Ubuntu:
[http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

+1 dood, that's some cool stuff :)

---

