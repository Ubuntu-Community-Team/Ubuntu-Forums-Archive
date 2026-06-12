---
title: "SSH Tunnels"
date: 2011-11-30
forum: The Cafe
---

### Post by steveodeevo on 2011-11-30
I have been playing around with SSH Tunnels (for legit reasons, not for bit torrents or anything else), and have noticed it is a bit slow at times and did some research into why, from what I have found it seems that the SSH buffers slow the whole thing down, and so I wondered if anyone had any input or experience on this.

I also wondered is it better say to launch a tunnel straight from the term, or from something like GSTM in terms of performance or is there no difference?

I did read some information about SSH2 Tunnels as well, however again the overall amount of information about this on the web seems limited and certainly doesn't really talk about any speed increases or performance.

Finally I found an article over at [http://forum.slicehost.com/comments.php?DiscussionID=3424](http://forum.slicehost.com/comments.php?DiscussionID=3424) which details using a high performance version of ssh which apparently gives about a 30% boost to the overall speed of an SSH Tunnel, but haven't tried it yet.

I did find an article talking about such a thing as a good idea for server editions, how ever I seem to have lost that link somewhere.

So anyone got any thoughts?

---

### Post by YeOK on 2011-11-30
I use an SSH tunnel to browse the web. Not for any real reason, I have done for a few years now. I actually find a number of sites are quicker on a tunnel; though I suspect its more of a routing issue. 

I start my tunnel with a gnome launcher, I make sure compression is enabled. I then have an extension in chrome that auto selects to either connect directly to a site or send the requests via a tunnel (Tunnel is default).

Why? I started a few years ago when I shared an internet connection with a flat mate, we both wanted to play some stupid web browser game and they restricted you to one account per IP. I guess I just got used to it, though I don't play any web based games now or share an internet connection.

---

### Post by steveodeevo on 2011-12-13
I have been playing with an SSH Tunnel setup on my network for a while now, I have one I purchased from a company over in the US ([http://www.ramhost.us](http://www.ramhost.us)) which I use for business purposes such as collecting email over an encrypted connection, I have to admit I originally set it up out of interest to see what could be done, and at $25 a year, it seemed worth a punt to play around with, i figured a paid one was more secure than a shared public one.

I have tried quite a few different things with it, from loading **Thunderbird** using **tsocks** to collect my email, through to routing **tor** through it (which I am amazed actually works, you put the tunnel down as the parent proxy server and it then only shows port 22 on the firewall, but still switches between severs on the Tor network!), to routing **skype** through it using **tsocks** and so on, I even got my internet TV on it at one point which is quite weird to see the different services offered in other regions!

I had my network setup to use one local tunnel on the main firewall box to connect client PCs to when wanting to use the tunnel, but this seems slow so eventually I switched back to just opening the tunnel on the local machine when needed.

My typical setup now is to have **gTSM** connected to the tunnel, with **polipo** running a HTTP proxy on port 8123 with a socks parent through to **Tor** on port 9050 which itself is set to use the Tunnel via Socks, this and **tsocks**/**torsocks** seems to allow pretty much anything to be used with these services, with **Tor** even resolving at the Tunnel end of things so all I see on my firewall here is 1 connection on port 22 to the US host.

I have noticed that servers such as netflix and pandora now also work again due to the US IP address I guess of the tunnel host, where as normally they are blocked over here in the UK, not that I have bothered using them as its all a bit too slow for that kind of thing.

Its kind of interesting to muck about with and see what can be done, but the speed sort of makes it too slow for much more than web browsing and emails in my opinion.

My last idea was to see if I could use **tsocks** to send email via the tunnel, using Tor to provide different IPs for each time the mail command was invoked, however it seems it still always shows my local Internet IP here so no luck so far with that!

---

### Post by HermanAB on 2011-12-13
Howdy,

I use a SSH tunnel in order to have a US IP address, since I live in Arabia at the moment.

These switches speeds it up a bit: -C -c blowfish

Other than that, you can experiment with your MTU size.  If you have a bad internet link, then a shorter MTU size may work better than a longer one.

---

### Post by steveodeevo on 2011-12-20
Well after reading up some more I thought I would post my latest SSH command which I use to establish the tunnel which seems to give fairly good results

```

ssh -2 -4 -M -N -T -x -D 1080 user@host -C -c blowfish -f

```which forces it to use SSH2 protocol apparently, with IP4 only, disables various unused settings of SSH, opens a dynamic port on the socks port of 1080 using blowfish and goes into the background enabling me to carry on using the term for other things.

This seems to work quite well.

On another note as my tunnel provider doesn't allow public keys to be used to authenticate, I did a search for a way to use a script to automate the process of setting up the tunnel, and found that "expect" provides nice functionality for this (see below).

```


expect -c 'spawn ssh -2 -4 -M -N -T -x -D 1080 user@host -C -c blowfish;expect password; send "[password]\n";interact'


```expect can be install using apt-get install expect.

Might be of some interest to someone.

---

