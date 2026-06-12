---
title: "Dansguardian Gui for whole network?"
date: 2007-02-21
forum: Ubuntu Christian Edition
---

### Post by andytof47 on 2007-02-21
Hi Love the script again Thumbs up

Just wondering how I can make the Dansguardian script block the whole network

this is my setup

internet------Router192.168.1.1--------(192.168.1.5)Dansguardian Box acting as an accesspoint(192.168.2.25)------------Wireless Clients


I might have seen it somewhere already on the forums to be honest buuuut I've been searching for ages and can't track down how to do it

So yeah I basically just want to have all the computers going through this dansguardian computer - It works a charm as is but just needs to do the same for the other computers in the home


Also I downloaded the Gui and am using it nicely but I was wondering if I intend to use the Beta Version of the new Gui what do I need to do e.g must I uninstall? if so how



Cheers and Keep Up the Good Work


May God Bless the Work (Really I mean that)

---

### Post by mhancoc7 on 2007-02-21
> **andytof47 said:**
> Hi Love the script again Thumbs up

Just wondering how I can make the Dansguardian script block the whole network

this is my setup

internet------Router192.168.1.1--------(192.168.1.5)Dansguardian Box acting as an accesspoint(192.168.2.25)------------Wireless Clients


I might have seen it somewhere already on the forums to be honest buuuut I've been searching for ages and can't track down how to do it

So yeah I basically just want to have all the computers going through this dansguardian computer - It works a charm as is but just needs to do the same for the other computers in the home


Also I downloaded the Gui and am using it nicely but I was wondering if I intend to use the Beta Version of the new Gui what do I need to do e.g must I uninstall? if so how



Cheers and Keep Up the Good Work


May God Bless the Work (Really I mean that)

Thanks for your kind words. I am glad to hear that you find it useful.

Take a look at this thread. I believe it should help you get things working.
[http://www.ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian](http://www.ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian)

As for the beta GUI just got to the following thread and download the latest version.
[http://www.ubuntuforums.org/showthread.php?t=355935](http://www.ubuntuforums.org/showthread.php?t=355935)

Then double click on the downloaded file and it will let you install it. It will overwrite your existing GUI so no need to uninstall first.

Hope that helps, Jereme

---

### Post by andytof47 on 2007-02-22
Thanks for the link but that is what I used to get it all running on the system initially and it works a treat on that system, but only on that system.


So there is one other thing,

Transparent Proxying

Transparent proxy is the main thing here - I have linux and windows users and Internet Explorer is too easy to adjust

Unfortunately the Tinyproxy in Synaptic is compiled without transparent proxying(as far as I can tell)  so I am trying to install version 1.7 onto my Ubuntu system but 

A) I can't find a .deb package can anyone make one with the transparent proxy function built in?

B) can someone tell me why when I installed 1.7 why it doesn't automatically start after I reboot (I believe it has something to do with the Debian/Ubuntu filesystem is this correct) 

So how can I make all the traffic filtered transparently?

Cheers again

---

### Post by mhancoc7 on 2007-02-22
Oh, sorry about that.

I am not sure then how to get it going the way you want. There are some other members here that are much better with the dansguardian/tinyproxy configuration than me. Hopefully they will see this.

God Bless, Jereme

---

### Post by tonhou on 2007-02-22
This is a transparent proxy setup (as outlined in link given above)

The other systems must have their proxy settings set in the browser to point to the ip address of the dansguardian system and port 8080.

In Firefox:

Check manual proxy configuration and add “your DG box ip address” in first box and “8080” in second
Then tick “Use this proxy server for all protocols”

There will be something similar in IE.

--Tony

---

### Post by nabberuk on 2007-02-24
a transparent proxy is transparent, the end user should not know he/she is going through it. meaning they shouldnt have to put anything in the proxy settings of the internet browser.

Am i correct in saying that?

---

### Post by tonhou on 2007-02-24
If you can't set and lock proxy settings for your browsers then this setup with Ubuntu CE is not for you.

A dedicated server using something like [ClarkConnect]("http://www.clarkconnect.com/") could be a much better option.

--Tony

---

### Post by andytof47 on 2007-02-25
Sadly you are wrong again 

I have it working and will write up a howto for the whole of the community - but you must make sure you have your facts straight before recomending a solution like clark connect:popcorn: 


Well when I write it up I hope you enjoy it

---

### Post by bobbarry on 2008-02-07
> **andytof47 said:**
>  ...I have it working and will write up a howto for the whole of the community...
Have you written that HOWTO, Andy?  I'd sure like to see it!

Ahhh - found it:
[http://ubuntuforums.org/showthread.php?p=2213171#post2213171](http://ubuntuforums.org/showthread.php?p=2213171#post2213171)

(Ubuntu Forums > The Ubuntu Forum Community > Other Community > Discussions > Tutorials & Tips > Network Content Filter)

Now to try it...

---

### Post by chris308 on 2008-02-08
Hi Andy,

I currently use Untangle as my transparent proxy server.  You may want to check them out at [http://untangle.com]("http://untangle.com")

It's very easy to setup.  All configuration is done via a very nice GUI.  I have PIII 550MHz box at home running as a internet proxy, protocol control, anti-spam and anti-virus filter.  Seems to be doing a good job with limited resources.

Best of luck and God bless,
Chris

---

