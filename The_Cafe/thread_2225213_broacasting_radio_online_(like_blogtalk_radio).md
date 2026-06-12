---
title: "broacasting radio online (like blogtalk radio)"
date: 2014-05-20
forum: The Cafe
---

### Post by netgooroo on 2014-05-20
Hey guys, 
I am wanting to continue my online presence through having my own "radio show" and I need to be able to do this in the easiest and most reliable way possible. 

When I did a search for "broadcasting online radio" I found this thread [http://ubuntuforums.org/showthread.php?t=73098](http://ubuntuforums.org/showthread.php?t=73098) But, it's a bit outdated and was hoping that we had something more up to date that we can use now. 

Ideally I am looking for something similar (NOT exactly the same) as blogtalk radio or, talkshoe that I can broadcast online with. I have done the shoutcast stuff way back in the day but, I want to focus more on the open source and free community if I am able to accomplish this through there. 

**ANY** help at all that helps to get me up and broadcasting is greatly appreciated. 

Thanks!

---

### Post by tgalati4 on 2014-05-20
Any help?  Well, I played with *mixx* a few years ago.  Haven't used it lately, so you will have to evaluate and let us know what you need and what is missing from *mixx*.

I also like [http://dynebolic.org](http://dynebolic.org) for a distro for creative outlaws.

---

### Post by netgooroo on 2014-05-20
> **tgalati4 said:**
> Any help?  Well, I played with *mixx* a few years ago.  Haven't used it lately, so you will have to evaluate and let us know what you need and what is missing from *mixx*.

I also like [http://dynebolic.org](http://dynebolic.org) for a distro for creative outlaws.


I appreciate the input but, I am looking to broadcast online..  **NOT** mixx audio...  Dunno how you got that mixed up but, thanks anyway. ;)

---

### Post by tgalati4 on 2014-05-20
You would typically set up an icecast server and use mixx to stream your content (including live vocals) out to the web.  dynebolic does this out of the box.  It is not as slick as tools available in Windows, but it generally works.

---

### Post by netgooroo on 2014-05-21
I'm downloading KXstudio 14.04 Kubuntu distro. It looks interesting. Hopefully there is some broadcasting apps in it. I don't need all the audio creation apps because the _only_ thing I'm intent on doing is broadcast online but, I can always use them if I need them.

---

### Post by HiImTye on 2014-05-21
if you're just looking to stream your voice, a basic icecast server is the simplest to set up.
if you're looking to stream music as well, mpd's httpd output doubles as an icecast/shoutcast server, so you can therefore run an icecast server with mpd as a fallback with very little setup needed. [here](http://amnezia.2f30.org/guides/icecast)'s an example of such a setup.

---

### Post by netgooroo on 2014-05-21
I've read up a little bit on icecast and it "sounds good" but, installing it and configuring it seems a bit daunting. I consider myself a fairly techy and knowledgable d00d but, reading how to set this stuff up makes me feel like I'm a n00b just installing Ubuntu for my very first time. **SHEESH!** I would love to find something that is "plug n play" out of the box. 

I did find a package called Internet DJ Console which "says" it streams online but, of course, you have to set up an icecast server in order to do that. I'm gettin to old to spend hours configuring apps just so I can broadcast an online radio show. maybe actually paying for something like blogtalk radio has it's advantages. *sigh* :-?

---

### Post by netgooroo on 2014-05-21
Update: I found this..  [Create your own online radio stream in Ubuntu ]("http://itblog.gr/630/create-your-own-online-radio-stream-in-ubuntu/") and I followed it exactly and, I'm still not able to get the stream up and running. 

On top of that, not sure how I would use it to do talk radio shows...  Again.. any help to accomplish this (hosting my own radio show on the net) would be greatly appreciated.

---

### Post by netgooroo on 2014-05-21
Update #2: I finally was able to get the stream "working" with icecast2 running in the background but, I am not able to hear any audio come through. I used Internet DJ Console and it worked great but, as I said, no audio coming from the stream. So, one step closer...  

Again, any help is appreciated.

---

### Post by tgalati4 on 2014-05-21
Open VLC on another machine and put in the network address for your stream.  Then use the error and message console to see what is happening.  Unfortunately Linux has a learning curve.  There is no way around that.

---

### Post by netgooroo on 2014-05-22
> **tgalati4 said:**
> Open VLC on another machine and put in the network address for your stream.  Then use the error and message console to see what is happening.  Unfortunately Linux has a learning curve.  There is no way around that.

That's a good idea..  I'll try that and thanks..  I been using Linux for many moons now so, I know my way around the command line. Just wish some stuff was more "simple" instead of having to get "down n dirty" with the code..  I'll update when I find out whats up.

---

### Post by netgooroo on 2014-05-22
So, I tried opening the stream in VLC as well as Rythembox and they both worked fine. What I mean by "worked" is that they did not report any errors or, were not able to connect to the stream. They both connected and ran the stream fine but, no audio at all was able to be heard. 

I have submitted a support request to the Internet DJ Console guys and am waiting to hear back from them.

Far as I can tell, everything is working as it should. I'm just not hearing any audio for some reason. 

I'll keep everyone updated just in case anyone is having any of the same issues. ;)

---

### Post by netgooroo on 2014-05-27
Hey guys...  so, I have went round and round with this icecast situation and, the support I get in the IRC chat room is that it sounds like it's a Internet DJ Console problem. I don't know if that's the fact of it or not as every time I run icecast and start IDJC, it shows the stream running just fine and I am able to play audio files just fine in addition to using all the settings. The only issue I seem to keep experiencing is not hearing the audio stream. 

I have looked for and not found any viable Internet DJ Console support options so far. Any one have any other suggestions??  This is getting old now after working on it for a week plus..  :?

---

