---
title: "Can javascript be crippled so it cannot leak IP?"
date: 2010-03-29
forum: Security
---

### Post by Ulysses_ on 2010-03-29
When using TOR it is recommended that you disable javascript and all other scripts because they can be used to detect your IP, defeating the purpose of TOR. But there are some sites that simply do not work without javascript. Is it possible to keep all javascript functionality but disable just the functionality that is used to leak your IP?

---

### Post by cdenley on 2010-03-29
> **Ulysses_ said:**
> When using TOR it is recommended that you disable javascript and all other scripts because they can be used to detect your IP, defeating the purpose of TOR. But there are some sites that simply do not work without javascript. Is it possible to keep all javascript functionality but disable just the functionality that is used to leak your IP?

Javascript won't reveal your IP, because any connections established by javascript will still be handled by your browser. Anything that is handled by a plugin (flash, java, etc), though, probably won't use your proxy settings, and can reveal your IP to any server it connects to. Javascript is often used for browser exploits, though.

I suggest using the noscript addon for firefox.
```

sudo apt-get install mozilla-noscript

```

---

### Post by Ulysses_ on 2010-03-29
Thanks, I'm already using noscript, the problem is some sites do not work without javascript.  TOR manuals say javascript should be disabled.  Is that not because it can be twisted to reveal the IP?

---

### Post by cdenley on 2010-03-29
> **Ulysses_ said:**
> Thanks, I'm already using noscript, the problem is some sites do not work without javascript.  TOR manuals say javascript should be disabled.  Is that not because it can be twisted to reveal the IP?

I don't think so, but disabling javascript may prevent other embedded objects which use plugins as I discussed. I know noscript does.

---

### Post by EJeanmaire on 2010-03-29
Someone correct me if I am wrong here, but I believe AJAX could return your IP or other bits of information about you to the server. AJAX being related to Javascript and JAVA.

---

### Post by cdenley on 2010-03-29
> **EJeanmaire said:**
> Someone correct me if I am wrong here, but I believe AJAX could return your IP or other bits of information about you to the server. AJAX being related to Javascript and JAVA.

I'm pretty sure AJAX is handled by the browser, so it would use the same proxy settings as used when browsing.

---

### Post by OpSecShellshock on 2010-03-29
Flash cookies might be able to do it, though (particularly if there are some left over from prior to the installation of TOR).

---

### Post by Ulysses_ on 2010-03-29
If all scripts/plugins/addons/extensions/whatever they are called are disabled and only javascript is enabled, is there any javascript trick to reveal the ip?

What if your ADSL router is at [http://192.168.2.1](http://192.168.2.1) and javascript from a web page attempts to load that page up and guess the name and password to log in to the router and read the ip from the status page?

---

### Post by cdenley on 2010-03-29
> **Ulysses_ said:**
> If all scripts/plugins/addons/extensions/whatever they are called are disabled and only javascript is enabled, is there any javascript trick to reveal the ip?

What if your ADSL router is at [http://192.168.2.1](http://192.168.2.1) and javascript from a web page attempts to load that page up and guess the name and password to log in to the router?

It would still be using your proxy settings (I'm pretty sure), and you can't connect to your router through tor.

---

### Post by slowth5 on 2010-03-29
A reverse DNS lookup doesn't require javascript, cookies, etc. 

From Steve Gibson's Shields Up site:

> The concern is that any web site can easily retrieve this unique "machine name" (just as we have) whenever you visit. It may be used to uniquely identify you on the Internet. In that way it's like a "supercookie" over which you have no control. You can not disable, delete, or change it. Due to the rapid erosion of online privacy, and the diminishing respect for the sanctity of the user, we wanted to make you aware of this possibility. Note also that reverse DNS may disclose your geographic location. 

[www.grc.com](www.grc.com)

---

### Post by doas777 on 2010-03-29
any client side scripting can identify you I am afraid.

---

### Post by cdenley on 2010-03-29
> **slowth5 said:**
> A reverse DNS lookup doesn't require javascript, cookies, etc.

What would they perform a reverse DNS lookup on? They need an IP first. The whole purpose of tor is to hide your IP. Of course cookies is an issue. I think privoxy is supposed to filter any cookies, or you should be able to disable them in the browser settings. Flash uses its own type of "cookies" as well, another reason not to use flash with tor.

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> What would they perform a reverse DNS lookup on? They need an IP first. The whole purpose of tor is to hide your IP. Of course cookies is an issue. I think privoxy is supposed to filter any cookies, or you should be able to disable them in the browser settings. Flash uses its own type of "cookies" as well, another reason not to use flash with tor.

I guess my point is I don't think anonymity is possible on the internet. This includes TOR. Traffic analysis, DNS leaks, eavesdropping on exit nodes...it's not anonymous.

---

### Post by OpSecShellshock on 2010-03-29
> **cdenley said:**
> What would they perform a reverse DNS lookup on? They need an IP first. The whole purpose of tor is to hide your IP. Of course cookies is an issue. I think privoxy is supposed to filter any cookies, or you should be able to disable them in the browser settings. Flash uses its own type of "cookies" as well, another reason not to use flash with tor.

Exactly. Hiding the IP address takes away the ability to (potentially) connect your browsing activity to the IP address that's been allocated to your web-facing equipment. All of the other things that can't be hidden (OS fingerprints, persistent sessions, saved website preferences, referrer headers, user-agent strings, and the like) still work, and potentially reveal even more than an IP address does. Browsing with cookies and scripts enabled undermines the entire point of using TOR.

---

### Post by cdenley on 2010-03-29
> **slowth5 said:**
> I guess my point is I don't think anonymity is possible on the internet. This includes TOR. Traffic analysis, DNS leaks, eavesdropping on exit nodes...it's not anonymous.

Tor alone hides your IP. No more, no less. There are solutions for those other issues, except traffic analysis if someone controls enough tor nodes.

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> Tor alone hides your IP. No more, no less. There are solutions for those other issues, except traffic analysis if someone controls enough tor nodes.

I'm suggesting that Tor doesn't hide your IP. Who else would you want to hide from but national organizations, which will undoubtedly have control of every node. The OP is worrying about javascript fingering his IP, while every packet is being monitored. Let's not delude ourselves. This is a false sense of security.

---

### Post by cdenley on 2010-03-29
> **slowth5 said:**
> I'm suggesting that Tor doesn't hide your IP. Who else would you want to hide from but national organizations, which will undoubtedly have control of every node. The OP is worrying about javascript fingering his IP, while every packet is being monitored. Let's not delude ourselves. This is a false sense of security.

"national organizations" have unlimited access to all tor nodes and actively analyze traffic to map what IP is sending what traffic? Anything to support this claim? By "national organizations" do you mean governments?

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> "national organizations" have unlimited access to all tor nodes and actively analyze traffic to map what IP is sending what traffic? Anything to support this claim? By "national organizations" do you mean governments?

Of course that's what I mean. Please tell me you're playing devil's advocate. Anonymity does not exist on the internet. There is always a weak link. In the case of Tor, it's the entrance and exit nodes.

---

### Post by OpSecShellshock on 2010-03-29
TOR isn't a security tool, it's a privacy tool. It hides the IP address of the device that initiates a connection from the device ultimately being connected to. As far as the destination is concerned, the connection is coming from the last TOR node.

For the entry points, someone would have to be capturing traffic between the home connection of the user and the first TOR node they connect to. To monitor all traffic passed through any provider's network, they'd have to be passively sniffing all traffic coming out of all homes. This would create so much stored data that it would be impossible to go through any of it in a meaningful way. Then the sniffing party would have to correlate the data leaving the point of origination with the data being delivered to the first TOR node (which they're presumably also sniffing and logging?), and continue doing that through the entire process. They'd have to do this for every connection to and from every node, as well as the various ultimate destinations. There isn't a body of any size with the authority to do that, or with the technological capability to do that, or with the human staff that would be required to give it meaning. Even leaving onion routing out of it altogether it's impossible to meaningfully intercept and analyze all traffic to and from every network device even in one particular ISP's enterprise or one government's jurisdiction. Sure, either of those entities could target one specific connection and passively listen, but there'd have to be a point to it.

---

### Post by slowth5 on 2010-03-29
Seems like we're missing the forest because of the trees. 

Let's assume you're hiding from the government. The government knows the purpose of Tor, so it joins the Tor network as an entry node. It watches you connect to the Tor network. It doesn't have to follow your traffic. Now there's probable cause. You've aroused the suspicion of the government. You're no longer anonymous. ;)

---

### Post by cdenley on 2010-03-29
> **slowth5 said:**
> Seems like we're missing the forest because of the trees. 

Let's assume you're hiding from the government. The government knows the purpose of Tor, so it joins the Tor network as an entry node. It watches you connect to the Tor network. It doesn't have to follow your traffic. Now there's probable cause. You've aroused the suspicion of the government. You're no longer anonymous. ;)

You don't have to control the entry node to determine someone is using tor. You only have to see their traffic. Using tor does not mean someone is doing something suspicious, or using the internet themselves. They can simply be another node. Usage of tor does not constitute probable cause of anything, other than being concerned about privacy (your own or others). You cannot join as an entry node. You join as a node. When a node receives traffic, it doesn't even know if they are the entry point. They would have to control A LOT of nodes then get really lucky to have most or maybe all your traffic get routed through their nodes (I think 5 hops?) and have a lot of resources to analyze a lot of traffic to match up a lot of complicated patterns.

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> You don't have to control the entry node to determine someone is using tor. You only have to see their traffic. 

In response to the assertion that monitoring all data on an ISP level is impossible, I proposed the government could sit on a Tor node. It will be an entry/exit node at some point. Maybe they are on an exit node and watch your email credentials pass by. Uh oh!

> Using tor does not mean someone is doing something suspicious, or using the internet themselves. They can simply be another node. Usage of tor does not constitute probable cause of anything, other than being concerned about privacy (your own or others).

Interesting perspective. Not sure about your government, but mine passively monitors all phone conversations for trigger words. This is well documented. Tor is used for anonymity. The government doesn't want you to hide things. It invokes terrorism or any number of justifications, and you are now suspect.

> You cannot join as an entry node. You join as a node. When a node receives traffic, it doesn't even know if they are the entry point. 

How would you not now? The IP is traceable. The node knows your IP. If you have reason to hide from the government, I'm sure your traffic is monitored at the ISP level anyway. They will know you're connecting to Tor. They will use any justification necessary to watch you like a hawk. I doubt the government thinks you're just using Tor to hide your visits to your favorite forum. 


> They would have to control A LOT of nodes then get really lucky to have most or maybe all your traffic get routed through their nodes (I think 5 hops?) and have a lot of resources to analyze a lot of traffic to match up a lot of complicated patterns.

We're getting caught up in the Tor protocol when that's not what I'm attacking.

---

### Post by cdenley on 2010-03-29
> **slowth5 said:**
> In response to the assertion that monitoring all data on an ISP level is impossible, I proposed the government could sit on a Tor node. It will be an entry/exit node at some point. Maybe they are on an exit node and watch your email credentials pass by. Uh oh!

As I said, tor only hides your IP. If you send e-mail credentials in plain text, you're at risk whether you're using tor or not. Who asserted that ISP level traffic monitoring is impossible? It is quite easy to for an ISP to monitor someone's traffic. They can easily determine if someone is part of the tor network. They cannot view their traffic.


> **slowth5 said:**
> 
Interesting perspective. Not sure about your government, but mine passively monitors all phone conversations for trigger words. This is well documented. Tor is used for anonymity. The government doesn't want you to hide things. It invokes terrorism or any number of justifications, and you are now suspect.

Tor protects your traffic from being matched to your IP. It does not hide the fact that you are part of the tor network. Nobody ever claimed it did.

> **slowth5 said:**
> 
How would you not now? The IP is traceable. The node knows your IP. If you have reason to hide from the government, I'm sure your traffic is monitored at the ISP level anyway. They will know you're connecting to Tor. They will use any justification necessary to watch you like a hawk. I doubt the government thinks you're just using Tor to hide your visits to your favorite forum. 

Plenty of people use tor that don't have reason to "hide from the government". Some people just value privacy. There are lots of tor users. They don't just protect themselves from eavesdropping, but also tracking. They don't want to reveal their IP to the servers they use. Was there ever any incident where usage of tor was used as probable cause of anything?


> **slowth5 said:**
> 
We're getting caught up in the Tor protocol when that's not what I'm attacking.

Then we can agree that tor makes it basically impossible (technically very, very improbable) for anyone to match your traffic from the exit node to your original IP, and combining it with other solutions can provide a reasonable level of anonymity? It is quite easy for an ISP or government to determine who is using tor (or encrypting traffic in any way), but the consequences you believe that may have depends how paranoid you are and what government conspiracy theories you subscribe to.

---

### Post by Ijan on 2010-03-29
> **Ulysses_ said:**
> Is it possible to keep all javascript functionality but disable just the functionality that is used to leak your IP?

From what I know I would guess - no, 

as this is what Torbutton tries and what you get using JavaScript-dependant sites with Torbutton is the result of this very effort.

So getting your JavaScript-sites to work would amount to something like a "better" rewrite of Torbutton or you had to specifically analyse the scripts of the sites you want to use and reconfigure your preferred JavaScript-filter on a per site basis.

Sounds like a lot of work, up to date technical knowledge into JavaScript and related possible privacy issues plus a personal consideration on these.

If only a few sites are concerned and you trust them you could consider simply whitelisting them.

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> Who asserted that ISP level traffic monitoring is impossible?

> **OpSecShellshock said:**
> For the entry points, someone would have to be capturing traffic between the home connection of the user and the first TOR node they connect to. To monitor all traffic passed through any provider's network, they'd have to be passively sniffing all traffic coming out of all homes. This would create so much stored data that it would be impossible to go through any of it in a meaningful way.


> Plenty of people use tor that don't have reason to "hide from the government". Some people just value privacy. There are lots of tor users. They don't just protect themselves from eavesdropping, but also tracking. They don't want to reveal their IP to the servers they use. 

I use a government as an example because they would have the necessary resources to track you down, if so desired. Bob in your internet forum will not track you down.

> Then we can agree that tor makes it basically impossible (technically very, very improbable) for anyone to match your traffic from the exit node to your original IP...

Yes, but that's not the point of my argument. The association with Tor removes the reality of anonymity, regardless of Tor's strength. You are now a person of interest, which means all bets are off.

> It is quite easy for an ISP or government to determine who is using tor (or encrypting traffic in any way), but the consequences you believe that may have depends how paranoid you are and what government conspiracy theories you subscribe to.

That's exactly my point. Thanks. I know my government monitors all data, so I wouldn't call that a conspiracy theory. Then again, I don't use Tor.

---

### Post by Ijan on 2010-03-29
> You are now a person of interest
That's maybe a bit overstated. Apart from paranoids and normal people googling for easter gifts via Tor there are enough governments that prosecute very basic stuff like porn, homosexuality, political information etc. providing a broad userbase and even broader potential userbase for Tor this way - for you to hide in though that beer can there to your right might be secretly filled with plutonium.

If your beloved leader has two enemies - you and your neighbour - and that bomb thread got posted using Tor, and you were using Tor and your neighbour wasn't that's a valid concern though.

It's always good - even necessary - to keep things in perspective dealing with relatives.

---

### Post by slowth5 on 2010-03-29
> **Ijan said:**
> That's maybe a bit overstated.

If you live in a country that controls all information, then no, that's not an overstatement. Using Tor could be grounds for execution due to treason. We can all agree a few countries that fit this description do exist, correct? Maybe they even house a significant population of the world? I can think of great examples.

I'm not talking about average Joe living under an average government that doesn't abuse its citizens. What I'm trying to say is that maybe those that need anonymity most can't access it because their government associates anonymity with dissent.

---

### Post by Ijan on 2010-03-29
Well sorry, this was already off-topic when I replied to you in a rather humorous intend but now it's getting even more out of focus as we mix a rather theoretical discussion with a personal and a moral perspective.

From a theoretical standpoint I would argue that monitoring all internet activity (or "all data" as you put it) in an industrialised country is probably by far not as easy as you seem to assume. Encryption as a means of privacy is e. g. a basic standard for all sorts of business communication and does not make you suspicious from the start.

If however - sadly - a personal risk can be involved with free communication in some countries, I would never dare to decide for a person if he/she should take or not take that risk no matter how big or small it was. 

Determining how big this risk might be and what could be the appropriate tools in a given situation to minimize that risk IMHO needs far more accurate information than so far present in this thread - especially if you touch the exceptional example of matters of life an death.

If you are interested in a discussion of such questions I would suggest you open a new thread.

---

### Post by cdenley on 2010-03-29
Anonymity does not mean hiding the fact that you are communicating at all, it means hiding who you are from the person you're communicating with, or any eavesdroppers who can read the conversation. There is a big difference between "ISP level traffic monitoring" and analyzing complex traffic patterns for HUGE amounts of encrypted traffic making hops all over the globe.

Nobody argues that you can hide the fact you're using tor. Is there somebody in this thread that lives in a country where people are persecuted by their government for using tor? If not, why are you making that point? Is there such a country? I don't think even China does that.

---

### Post by slowth5 on 2010-03-29
> **cdenley said:**
> Anonymity does not mean hiding the fact that you are communicating at all, it means hiding who you are from the person you're communicating with, or any eavesdroppers who can read the conversation. There is a big difference between "ISP level traffic monitoring" and analyzing complex traffic patterns for HUGE amounts of encrypted traffic making hops all over the globe.

Nobody argues that you can hide the fact you're using tor. Is there somebody in this thread that lives in a country where people are persecuted by their government for using tor? If not, why are you making that point? Is there such a country? I don't think even China does that.

I know the point of Tor. I'm trying to make a point that just using the program could arouse suspicion, and all I get is a rehash of the purpose of Tor. It was just a thought. Fodder for an interesting discussion. Chill out,and forget it.

---

### Post by Ulysses_ on 2010-03-30
This is an interesting discussion alright.  > Anonymity does not mean hiding the fact that you are communicating at all, it means hiding who you are  Any thoughts how you can also hide the fact that you are communicating?  Is it possible to hide TOR streams inside video streams in a manner that cannot be proven?

---

### Post by Ulysses_ on 2010-03-30
> **Ijan said:**
> this is what Torbutton tries and what you get using JavaScript-dependant sites with Torbutton is the result of this very effort.

So getting your JavaScript-sites to work would amount to something like a ''better'' rewrite of Torbutton

So are you saying javascript alone can reveal your IP?

---

### Post by doas777 on 2010-03-30
> **Ulysses_ said:**
> So are you saying javascript alone can reveal your IP?

yes.

remember, all traditional web technologies are "server side" meaning any processing happens on the server, and the output document is sent down to your PC. 

this is not enough for most websites these days however, so javascript was invented. instead of running on the server, it runs on your PC. thats what makes it special. since it is running on your PC instead of the server, it can do things like query your IP (though the scripter would have to get creative; it's not like you can run 'ifconfig' straight from javascript).

---

### Post by Ijan on 2010-03-30
> **Ulysses_ said:**
> Any thoughts how you can also hide the fact that you are communicating?Is it possible to hide TOR streams inside video streams in a manner that cannot be proven?
Hm, what would you count as hiding that you are communicating?  Communicating totally hidden or steganographicaly e. g. by means of [covert channels](http://en.wikipedia.org/wiki/Covert_channel) or just unobtrusive communitcation?

BTW: If you don't relay traffic through your Tor-client and use a non-public bridge, slowth5 is yet to explain how it is so extremely obtrusive as the Tor-projects website states that the traffic to the entry point does not look so very different from e. g. a browser talking to Apache via https.

> So are you saying javascript alone can reveal your IP?
No, that was just guessed. I don't have a qualified opinion on the individual JavaScript privacy issues discussed in the Torbutton documentation. IIRC stuff like profiling your system via JavaScript for later identification or reloading stuff after you switched Tor off is seen as a problem. There is however AFAIK no easy "hey JavaScript give me that public IP"-command if you mean that.

---

### Post by cdenley on 2010-03-30
> **Ijan said:**
> 
BTW: If you don't relay traffic through your Tor-client and use a non-public bridge, slowth5 is yet to explain how it is so extremely obtrusive as the Tor-projects website states that the traffic to the entry point does not look so very different from e. g. a browser talking to Apache via https.

I think the traffic alone makes it difficult to distinguish between https and tor traffic, but given the destination IP, it wouldn't be difficult to determine whether that server is a tor node.
[http://torstatus.kgprog.com/](http://torstatus.kgprog.com/)

---

### Post by Ijan on 2010-03-30
The bridges are not on that list. They are AFAIK given out one at a time over different channels and with regard to not having to much of them given to a specific IP range and such.

This is however seen as an anti-blocking measure and of course *not* promoted as a means of reliable secrecy. I meant this just as a remark to the above statements.

---

### Post by doas777 on 2010-03-30
[http://javascript.internet.com/user-details/ip-address.html](http://javascript.internet.com/user-details/ip-address.html)
[http://www.hashemian.com/tools/visitor-IP.htm]("http://javascript.internet.com/user-details/ip-address.html")

---

### Post by cdenley on 2010-03-30
> **doas777 said:**
> [http://javascript.internet.com/user-details/ip-address.html](http://javascript.internet.com/user-details/ip-address.html)

That doesn't use javascript to retrieve the IP, only to display the IP. The IP is retrieved on the server using SSI. It would be the IP of the tor exit node for someone using tor.

---

### Post by slowth5 on 2010-03-30
If someone had control of an entry node, then they would know you were using Tor. I know node determination is random, and I doubt it's possible to force a perpetual entry node, so the ip gathering would be random. If there were one subject in mind, it would be a waiting game. Does anyone know the average number of servers?

Again, I'm just exploring vulnerabilities. I'm not commenting on the feasibility of exploiting the vulnerabilities.

---

### Post by doas777 on 2010-03-30
> **cdenley said:**
> That doesn't use javascript to retrieve the IP, only to display the IP. The IP is retrieved on the server using SSI. It would be the IP of the tor exit node for someone using tor.

javascript is a client side technology, that is why it is embedded into the markup itself, rather than run in traditional binaries on the server. 
the javascript is packaged in the html output, and sent down to the client. the client receives the page and runs the scripts in a local context using the browsers scripting engine. 

if it's serverside, why bother using javascript at all?

---

### Post by cdenley on 2010-03-30
> **doas777 said:**
> javascript is a client side technology, that is why it is embedded into the markup itself, rather than run in traditional binaries on the server. 
the javascript is packaged in the html output, and sent down to the client. the client receives the page and runs the scripts in a local context using the browsers scripting engine. 

if it's serverside, why bother using javascript at all?

Did you actually read the links you posted?
```


<!-- ONE STEP TO INSTALL IP ADDRESS:

  1.  Copy the coding into the HEAD of your HTML document  -->

<!-- STEP ONE: Paste this code into the HEAD of your HTML document  -->

<HEAD>

<SCRIPT LANGUAGE="JavaScript">

<!-- This script and many more are available free online at -->
<!-- The JavaScript Source!! http://javascript.internet.com -->

<!-- Begin
// http://www.kdcgrohl.com

// Depending on your server set-up,
// you may need to use the ".shtml"
// extension [instead of the "html"
// or "htm"] as [B]the script uses Server
// Side Includes[/B]. To display in the
// title bar, exclude the
//"<title></title>" code from the page.

// This part gets the IP
var ip = '**[COLOR="Red"]<!--#echo var="REMOTE_ADDR"-->[/COLOR]**';

// This part is for an alert box
alert("Your IP address is "+ip);

// This part is for the status bar
window.defaultStatus = "Your IP address is "+ip;

// This part is for the title bar
document.write("<title>Your IP address is "+ip+"</title>");
//  End -->
</script>


<p><center>
<font face="arial, helvetica" size"-2">Free JavaScripts provided<br>
by <a href="http://javascriptsource.com">The JavaScript Source</a></font>
</center><p>

<!-- Script Size:  1.09 KB -->

```

The red part will NOT be seen by the browser. It will be replaced by the server with the IP the server sees (tor exit node). If SSI is not supported, then "<!--#echo var="REMOTE_ADDR"-->" will be printed instead of an IP.

I agree. That javascript is rather pointless. Why post it?

---

### Post by cdenley on 2010-03-30
> **slowth5 said:**
> If someone had control of an entry node, then they would know you were using Tor. I know node determination is random, and I doubt it's possible to force a perpetual entry node, so the ip gathering would be random. If there were one subject in mind, it would be a waiting game. Does anyone know the average number of servers?

Again, I'm just exploring vulnerabilities. I'm not commenting on the feasibility of exploiting the vulnerabilities.

It would be possible to identify IP's of systems which belong to the tor network. We have already established that. The user can use a bridge, which would make it more difficult since there isn't a complete list of bridges available, but it probably wouldn't be difficult to identify whether a given server is functioning as a bridge or a router on the tor network.

---

### Post by Ulysses_ on 2010-03-30
Can someone tell me what server-side language this is an include for?  Off-topic: some claim ASP can get your real IP (using the server-side command below) and there's nothing you can do about it because it is server-side.  Are they right?
```

[URL="http://www.wilderssecurity.com/showthread.php?t=223112"]

``` 
http://www.wilderssecurity.com/showthread.php?t=223112[/URL]

---

### Post by cdenley on 2010-03-30
> **Ulysses_ said:**
> Can someone tell me what server-side language this is an include for?  Off-topic: some claim ASP can get your real IP (using the server-side command below) and there's nothing you can do about it because it is server-side.  Are they right?    [http://www.wilderssecurity.com/showthread.php?t=223112](http://www.wilderssecurity.com/showthread.php?t=223112)

No programming involved. Just simple substitution.
[http://httpd.apache.org/docs/2.2/howto/ssi.html](http://httpd.apache.org/docs/2.2/howto/ssi.html)

When you're using tor, the server cannot see your real IP. That is the whole point! The server sees the IP of the tor exit node. The server cannot see your IP.

---

### Post by doas777 on 2010-03-30
> **cdenley said:**
> Did you actually read the links you posted?


didn;t like that one?
ok, throw some java in the mix (most modern browsers have a java plugin):
```


function GetIPAddress() {
  var ip = java.net.InetAddress.getLocalHost();
  var ipStr = new java.lang.String(ip.getHostAddress());
  var notifyString;
  return(notifyString);
}
```

---

### Post by cdenley on 2010-03-30
> **doas777 said:**
> didn;t like that one?
ok, throw some java in the mix (most modern browsers have a java plugin):
```


function GetIPAddress() {
  var ip = java.net.InetAddress.getLocalHost();
  var ipStr = new java.lang.String(ip.getHostAddress());
  var notifyString;
  return(notifyString);
}
```

Yes. As I already said, you have to be careful with any plugins such as java or flash. I'm not sure whether untrusted flash animations or java applets can simply retrieve the IP like that, but they can definitely send queries which may not use the browser's proxy settings.

---

### Post by OpSecShellshock on 2010-03-30
In any case, javascript can be used to get things that are even more useful than IP addresses. It might or might not be possible for the remote server to absolutely associate whatever information it obtains with the real home IP address on the client side (depending on whether it thinks it's communicating with the exit node or with the actual client computer). Most of the time, though, being able to do so isn't necessary. If you want to propagate malicious code or hijack persistent session data, you don't need the real IP address. If you plan to prosecute someone for criminal activity on the Internet, then you need way more than just an IP address. If you're enforcing company usage policy, you'll know who's using TOR before the traffic ever hits your gateways (seriously people, don't try to use TOR as a means of circumventing workplace security policies; it's very dumb).

---

### Post by Ulysses_ on 2010-03-30
java.net.InetAddress.getLocalHost();

What does the above return if my computer is behind an ADSL router using NAT?    The same as ifconfig?  Then it won't work.    

Otherwise, how does it discover my external IP?

---

### Post by Ulysses_ on 2010-03-30
> **OpSecShellshock said:**
> If you want to propagate malicious code or hijack persistent session data, you don't need the real IP address.

Remember I am only interested in enabling javascript and nothing else, is javascript enough to get malicious code that runs without permission in order to reveal other personal data?

---

### Post by Ulysses_ on 2010-03-30
> **OpSecShellshock said:**
> If you're enforcing company usage policy, you'll know who's using TOR before the traffic ever hits your gateways (seriously people, don't try to use TOR as a means of circumventing workplace security policies; it's very dumb).

On the other hand, not every company is large enough to have an official security policy.  Consider the possibility that people posting here about TOR are more senior than those responsible for networking.  You wouldn't tell your boss to stop using TOR would you.

---

### Post by OpSecShellshock on 2010-03-30
> **Ulysses_ said:**
> Remember I am only interested in enabling javascript and nothing else, is javascript enough to get malicious code that runs without permission in order to reveal other personal data?

If some javascript is written to obtain that data without TOR, then it can get most of it with TOR. The IP address might be incorrect, but everything else it gathers would be the same.

---

