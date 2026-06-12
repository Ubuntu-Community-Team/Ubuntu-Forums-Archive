---
title: "mp3 &amp; aac licensing"
date: 2011-04-04
forum: The Cafe
---

### Post by javajeff1 on 2011-04-04
Does anyone know why I have to agree to terms to install mp3 and aac plugins?

---

### Post by Chronon on 2011-04-04
When you buy a track from iTunes, you have paid for a copy of a copyrighted work.  This is separate from licensing issues surrounding patent-encumbered technologies that may be associated with the file format.

---

### Post by javajeff1 on 2011-04-04
The point I am making is that Apple must have paid any other fees that allow their members to play the music.

---

### Post by uRock on 2011-04-04
Not a support question. Moved to Cafe.

---

### Post by Chronon on 2011-04-04
> **javajeff1 said:**
> The point I am making is that Apple must have paid any other fees that allow their members to play the music.

What makes you conclude this?  DVDs do not contain patent licensing fees concerning the decoding and playback of the media.  That cost is assumed to be borne by whatever playback device/software you use to play back the media.  I am sure that the situation is identical here.

---

### Post by javajeff1 on 2011-04-04
> **Chronon said:**
> What makes you conclude this?  DVDs do not contain patent licensing fees concerning the decoding and playback of the media.  That cost is assumed to be borne by whatever playback device/software you use to play back the media.  I am sure that the situation is identical here.

Your logic implies that all companies with mp3 or aac players pay licensing fees.  That includes Windows Media player, itunes, car stereo manufacturers, etc.  I can understand that since Microsoft and Apple likely pay on the player side.  I originally thought the fees were on the encoder side.

---

### Post by Chronon on 2011-04-04
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)
[http://en.wikipedia.org/wiki/Advanced_Audio_Coding#Licensing_and_patents](http://en.wikipedia.org/wiki/Advanced_Audio_Coding#Licensing_and_patents)

Here are licensing rates for AAC:
[http://www.vialicensing.com/licensing/aac-fees.aspx](http://www.vialicensing.com/licensing/aac-fees.aspx)

I don't know how Foobar2k deals with these issues.

--
Part of the cost of most digital audio players is patent fees to Fraunhoffer et. al. for MP3 codec.  The patent holders don't seem as aggressive against free (gratis) decoders, but do enforce patents against audio player manufacturers.  (We are talking about patents in the USA.)

---

### Post by youbuntu on 2011-04-04
> **Chronon said:**
> [http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)
[http://en.wikipedia.org/wiki/Advanced_Audio_Coding#Licensing_and_patents](http://en.wikipedia.org/wiki/Advanced_Audio_Coding#Licensing_and_patents)

Here are licensing rates for AAC:
[http://www.vialicensing.com/licensing/aac-fees.aspx](http://www.vialicensing.com/licensing/aac-fees.aspx)

I don't know how Foobar2k deals with these issues.

--
Part of the cost of most digital audio players is patent fees to Fraunhoffer et. al. for MP3 codec.  The patent holders don't seem as aggressive against free (gratis) decoders, but do enforce patents against audio player manufacturers.  (We are talking about patents in the USA.)

Wow! They're not greedy, are they!

---

### Post by javajeff1 on 2011-04-04
Foobar 2000 and Rhythm box would both qualify as free decoders then.  I do not see how either website has a place for an individual to buy their own license.  I think anyone would be willing to pay $1 for a license to play mp3 on Rhythm box.

[http://www.mp3licensing.com/royalty/](http://www.mp3licensing.com/royalty/)

If they go after the free stuff, they risk the format going away permanently.  I could easily use ogg if some of my devices used it.

---

### Post by SeijiSensei on 2011-04-04
You can buy a license for gstreamer-based codecs from [Fluendo]("http://www.fluendo.com/").

If you think the miniscule number of people using "free stuff" represents any sort of threat to the dominance of patent-encumbered technologies like MP3, ask the next ten people you meet if they know what an "MP3" is.  Then ask about "Ogg Vorbis" or "FLAC."  They may not know exactly what MP3 means, but I'm betting most of them will have heard the term before.  Ogg?  Don't think so.

---

### Post by Chronon on 2011-04-04
> **javajeff1 said:**
> Foobar 2000 and Rhythm box would both qualify as free decoders then.  I do not see how either website has a place for an individual to buy their own license.  I think anyone would be willing to pay $1 for a license to play mp3 on Rhythm box.

[http://www.mp3licensing.com/royalty/](http://www.mp3licensing.com/royalty/)

If they go after the free stuff, they risk the format going away permanently.  I could easily use ogg if some of my devices used it.
I believe that the responsiblity lies not with the end user but with whoever distributes a codec.  If I understand correctly, this is the reason that LAME and some other encoders do not distribute binaries.  

You are correct that the proliferation of these formats helps the patent holders profit.

As SeijiSensei says, you can buy licensed codecs:
[http://shop.canonical.com/index.php?cPath=19](http://shop.canonical.com/index.php?cPath=19)

---

### Post by javajeff1 on 2011-04-05
I would be happy to pay $1 per software title that I use, but it does not seem to be set up for me to do that.  I want to use open source or freeware programs to play music.

Correct me if I am wrong, but anyone is required to covert all music that they purchase on Amazon MP3 to ogg in order to use it on Ubuntu?

---

### Post by SeijiSensei on 2011-04-05
> **javajeff1 said:**
> I would be happy to pay $1 per software title that I use, but it does not seem to be set up for me to do that.

It's not set up that way because you are licensing the *codecs*, not the programs.  That's actually a better model since the one license applies to any software program you use, as long as it runs GStreamer codecs.

> I want to use open source or freeware programs to play music.

Unfortunately what you want and what's legal are two different things.  That's just a fact of life that isn't going to change regardless of your feelings on the matter.

> Correct me if I am wrong, but anyone is required to covert all music that they purchase on Amazon MP3 to ogg in order to use it on Ubuntu?

You're not "required" to do anything.  If you want to listen to MP3's legally in a jurisdiction which recognizes software patents, you need to license the codec.  If you don't live in such a place, or you choose to ignore the legalities involved, you can use free players and let them download the codecs for you.  KDE programs like Amarok or K3b notify the user when they first run that you're using a version with limitations on which formats they support.  Then they give you the option of installing the missing codecs.  This is a reasonable solution since it lets people in countries where software patents aren't enforceable obtain the codecs they need.  For those of us living under a different legal regime, you can still obtain the codecs, but the legal onus is on you, not on Canonical.

I don't know there's much more we can tell you about this.

---

### Post by javajeff1 on 2011-04-05
Thanks for the insight.  I was just curious since I buy music online.  I rip my CDs to flac.

---

