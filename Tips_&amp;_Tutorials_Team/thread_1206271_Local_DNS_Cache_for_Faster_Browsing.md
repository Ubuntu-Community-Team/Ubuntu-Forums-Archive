---
title: "Local DNS Cache for Faster Browsing"
date: 2009-07-03
forum: Tips &amp; Tutorials Team
---

### Post by tad1073 on 2009-07-03
[FONT=Arial][SIZE=3]This tutorial was taken directly from:
[http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/)
[/SIZE][/FONT]
[FONT=Arial][SIZE=3]A DNS server resolves domain names into IP addresses. So when you request “google.com” for example, the DNS server finds out the address for the domain, and sends your request the right way. [/SIZE][/FONT]
 [FONT=Arial][SIZE=3]
You can run a DNS cache on your computer. This will speed up the process of looking up domain names when browsing. The difference is about 30-60 ms for me. Multiply that difference by the number of websites you visit a day for an approximate estimate of the speed improvement. Of course, all this would be worth it if it weren’t for the fact that setting this up is way too easy.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]
The following instructions are for someone with a cable (broadband) internet connection, where the computer gets it’s local IP address using DHCP from the router in your house/office:[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]
The package we will be using for caching nameserver lookups is called [/SIZE][/FONT][FONT=Arial][dnsmasq]("http://packages.ubuntu.com/dnsmasq").[/FONT][FONT=Arial][SIZE=3] So first, install it using:

```
$sudo apt-get install dnsmasq
```(If you can’t find then, then you probably haven’t added the Universe repository to your list of repositories.)[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]
No uncomment the following line (that is edit the line to NOT have a “#” in the beginning) in the file /etc/dnsmasq.conf:

```
listen-address=127.0.0.1
```[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]
Now edit /etc/dhcp3/dhclient.conf and make sure the section below exactly like this, especially the line that says “prepend domain-name-servers 127.0.0.1;”

```
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope;
```[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]
Explanation for the above change: In the normal case, when you get a new dhcp lease, the dhcp3 client (tool) on your computer gets a new lease, and updates the /etc/resolv.conf file on your computer with the right values for the DNS servers to use (usually some machine in the network of your hosting provider). Adding the “prepend” option as we did above ensures that “127.0.0.1&#8243; will appear on the top of the list of DNS servers. That magic number refers to your own computer. So in the future, whenever your computer needs to resolve a domain name, it will forward that request to dnsmasq (which is running at 127.0.0.1 – your computer). If the details for the domain name are already in you cache, well and good, dnsmasq will serve it up and make the process real fast. If it is not in the cache, then dnsmasq will look at the /etc/resolv.conf file and use the nameservers listed below the “127.0.0.1&#8243;. I hope that explains things.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]
Now open the file /etc/resolv.conf in your text editor.  It probably looks like:

```
search yourisp.com
nameserver 217.54.170.023
nameserver 217.54.170.024
nameserver 217.54.170.026
```[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]
The 127.0.0.1 is missing right now since you haven’t renewed your lease after you edited the /etc/dhcp3/dhclient.conf file. So, let us add that in manually this one time. After you do, your /etc/resolv.conf file will look like the following:

```
search yourisp.com
nameserver 127.0.0.1
nameserver 217.54.170.023
nameserver 217.54.170.024
nameserver 217.54.170.026
```Don’t worry if the numbers are different – if they are not, then hey – we must be neighbours [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_wink.gif[/IMG][/SIZE][/FONT]  
 [FONT=Arial][SIZE=3]
Okay. We are almost done here. All we have to do now is to restart dnsmasq so that the changes we made to the configuration file take effect. You can do that using the command:

```
$sudo /etc/init.d/dnsmasq restart.
```[/SIZE][/FONT] [FONT=Arial][SIZE=3]

Now you are running a local DNS cache. If you want to measure your speed improvement, type the command:

```
$dig google.com
```You will see something like “;; Query time: 38 msec” there.
Now type the command again, and you should see something like:”;; Query time: 2 msec”[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]
See, the first time, since google.com’s details were not in your cache (you are using it for the first time), the query took 38 ms. The second time, the cache speeds up the lookup. I have been using this for over a month now, and haven’t had a problem.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3][B]
The following is ONLY for dsl customers[/B]

Note: If you have a dsl connection, the following may work:
Basically, the differences are in how the “conf” files are edited and used.

Copy the /etc/resolv.conf file to /etc/resolv.dnsmasq.conf
Then, edit the /etc/dnsmasq.conf file as follows:

```
# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
resolv-file=/etc/resolv.dnsmasq.conf
```You also have to uncomment the line that says listen-address=127.0.0.1

Now, edit /etc/resolv.conf to have ONLY the following line in it:

```
nameserver 127.0.0.1
```Next, edit /etc/ppp/peers/dsl-provider and change the line:
usepeerdns to

```
#usepeerdns
```(that is, comment out that line)

The ppp client does not allow you to prepend the 127.0.0.1 entry to your /etc/resolv.conf file. So what we did in the above was to create a copy of your previous resolv.conf for dnsmasq to use for lookups, update the file to use a local cache, and then prevent the ppp client from overwriting the resolv.conf file the next time. Now you can restart the dnsmasq service as I explained above, and start enjoying faster name resolution.
[/SIZE][/FONT]    
[FONT=Arial][SIZE=3]
[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Now, if it doesn't work for some reason, just reverse the steps to get your original configuration back.

And as always ----- **[SIZE=5]BACK-UP YOU FILES[/SIZE]**
 [/SIZE][/FONT]

---

### Post by jpeddicord on 2009-07-07
What should be done with this? I'd approve it readily if it wasn't just a direct copy-paste from the linked article. To the poster's credit, he did properly cite the source, but should we really allow people to just copy/paste article for tutorial credit?

---

### Post by jpeddicord on 2009-07-07
Second thought from IRC, this is in the T&T criteria:

> In the case that a thread is not accepted into this section, it will be moved to an appropriate area. Refused tutorials are not deleted or jailed, unless they are duplicates or violate forum policy.

This technically is a duplicate, even if the original content is from another site. His post might qualify under fair use, but you never know if the original author really wants their content copied verbatim.

Going to move to jail on these grounds and PM the poster to let them know.

---

### Post by jpeddicord on 2009-07-07
WOOOOSH!

I completely missed item #7 in the criteria:

"Tutorials may not be copy-and-pasted from outside sources."

Right, carry on. :lolflag:

---

### Post by cariboo on 2009-07-07
I pm'd the op a couple of days ago and asked if he was the original author, or if he had just copied and pasted it, and suggested that it didn't meet the criterea if he wasn't the author. I have heard from yet.

---

