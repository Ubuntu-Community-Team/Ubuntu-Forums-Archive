---
title: "Will the music lens be in 12.04 final?"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-13
So as far as I know, the music lens hasn't worked at all since banshee was replaced with rhythmbox because it is still tied to banshee.

So the question is, will the music lens actually be working by release time or is it another thing to be left for next time?

---

### Post by mc4man on 2012-03-13
I saw a bug report that indicated it will, can't imagine they'd release "precise" without one

---

### Post by x-shaney-x on 2012-03-13
It would be a very odd decision to change the default music player and leave a major part of the dash completely dead and useless.

---

### Post by mc4man on 2012-03-13
The bug I saw, still active, was in OO concerning adding scopes for other players which then included rhythmbox.
Not too long ago it was mentioned that rhythmbox support would be coming before release

---

### Post by grahammechanical on 2012-03-13
If you upgrade an 11.10 with banshee to 12.04 as I did back in November you will get a sound app indicator that has both Banshee and Rhythmbox in the menu. Either application will play music files and the music files that are played are picked up by the Music lens in the Dash.

A fresh install of 12.04 will give you Rhythmbox only. The music files that you play with Rhythmbox will be picked up by the Dash Music lens.

This has been my actual experience from using 12.04 since November.

Right now I am using 12.04 and I can press Super+M and the Dash Music lens opens and I see the last songs that I played through Rythmbox, the albums they came from, and suggestions of songs available for download.

So, you are not correct to say 

> the music lens hasn't worked at all since banshee was replaced with rhythmbox because it is still tied to banshee

You are spreading FUD. Fear, Uncertainty and Doubt.

Download the ISO and try it out as live CD just as anyone is advised to do before installing Ubuntu.

For the record, I have 3 times participated in official tests of Unity including the integration of the Music lens and Rhythmbox.

Regards.

---

### Post by mc4man on 2012-03-13
Sorry - I have 2 new installs, beta 1 & yesterdays image - on neither one will any tracks show up on the music lens, played or otherwise, played half a dozen in rhythmbox
(One shouldn't need to play a track to see in the music lens

They do show in the files lens, either straightup if recent or under the audio filter.

So don't see the lens working in the absence of banshee or some other?? user intervention 

The only thing searches produce is purchase results

---

### Post by mc4man on 2012-03-13
Anyway  - here's the bug I mentioned, comment 16 is appropriate to precise

[https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/839319](https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/839319)

---

### Post by x-shaney-x on 2012-03-16
> **grahammechanical said:**
> A fresh install of 12.04 will give you Rhythmbox only. The music files that you play with Rhythmbox will be picked up by the Dash Music lens.
I have done 3 fresh installs of 12.04 at various times during it's development.  Music files haven't shown up in the music lens in any of them.

> You are spreading FUD. Fear, Uncertainty and Doubt.
In my defence, I said "as far as I know" since my statement is based on what I have read on the subject.  I am not stating it as fact.

---

### Post by screaminj3sus on 2012-03-16
> **grahammechanical said:**
> If you upgrade an 11.10 with banshee to 12.04 as I did back in November you will get a sound app indicator that has both Banshee and Rhythmbox in the menu. Either application will play music files and the music files that are played are picked up by the Music lens in the Dash.

A fresh install of 12.04 will give you Rhythmbox only. The music files that you play with Rhythmbox will be picked up by the Dash Music lens.

This has been my actual experience from using 12.04 since November.

Right now I am using 12.04 and I can press Super+M and the Dash Music lens opens and I see the last songs that I played through Rythmbox, the albums they came from, and suggestions of songs available for download.

So, you are not correct to say 



You are spreading FUD. Fear, Uncertainty and Doubt.

Download the ISO and try it out as live CD just as anyone is advised to do before installing Ubuntu.

For the record, I have 3 times participated in official tests of Unity including the integration of the Music lens and Rhythmbox.

Regards.

I have a fresh install of beta 1 (with updates). The music lense doesn't work AT ALL. and it has never worked for me since the rhythmbox switched.

At the very least it seems broken for many people atm.

---

### Post by cariboo on 2012-03-16
There was a [Rhythmbox scope]("https://code.launchpad.net/~markjtully/+junk/rhythmbox-scope-precise") package in the repositories, about a week ago, but it wanted to remove Unity, so I didn't try it. Hopefully it gets rebuilt to work with the latest version of Precise.

---

### Post by Framli on 2012-03-16
The updated Music lens with Rhythmbox integration (it will keep Banshee integration by default too) should land next week. ;)

---

### Post by Gregory Lee on 2012-03-17
Do I have, or will I get, lenses with the Gnome 3 shell?

---

### Post by x-shaney-x on 2012-03-17
No, lenses are part of unity.  Unless shell comes up with something similar to show them.  Extension maybe?

---

### Post by x-shaney-x on 2012-03-23
I notice that the lens is working (mostly) after todays updates.
Included filters to show either banshee or rhythmbox as sources.

Unfortunately, the music files shown don't include album art, the way they did in 11.10, just a generic music file mimetype kind of icon.
Hope that also gets sorted for release.

---

### Post by screaminj3sus on 2012-03-23
Working here as well with rhythmbox now, but I have the same album art issue.

---

### Post by mc4man on 2012-03-24
It also works pretty good here though looking at the genre's the choices are interesting I guess.
There are 15 'sections' that account for 41 genre's, so obviously a line was drawn somewhere.
For the curious these are the ones chosen - 'other' becomes a catch all 
 ```
   /* blues */
      map.set (BLUES_ID, "blues");

      /* classic */
      map.set (CLASSIC_ID, "classic");
      map.set (CLASSIC_ID, "classical");

      /* country */
      map.set (COUNTRY_ID, "country");

      /* disco */
      map.set (DISCO_ID, "disco");

      /* funk */
      map.set (FUNK_ID, "funk");

      /* rock */
      map.set (ROCK_ID, "rock");
      map.set (ROCK_ID, "heavy");
      map.set (ROCK_ID, "hard");

      /* metal */
      map.set (METAL_ID, "metal");
      map.set (METAL_ID, "heavy");

      /*hip hop */
      map.set (HIPHOP_ID, "hip-hop");

      /*house*/
      map.set (HOUSE_ID, "house");
      map.set (HOUSE_ID, "chillout");
      map.set (HOUSE_ID, "minimal");
      map.set (HOUSE_ID, "hard");
      map.set (HOUSE_ID, "electronic");

      /*new wave*/
      map.set (NEWWAVE_ID, "new-wave");

      /*r-and-b*/
      map.set (RANDB_ID, "r-and-b");

      /*punk*/
      map.set (PUNK_ID, "punk");
      map.set (PUNK_ID, "punk rock");
      map.set (PUNK_ID, "hardcore");
      map.set (PUNK_ID, "heavy");

      /*jazz*/
      map.set (JAZZ_ID, "jazz");

      /*pop*/
      map.set (POP_ID, "pop");
      
      /*reggae*/
      map.set (REGGAE_ID, "reggae");

      /*soul*/
      map.set (SOUL_ID, "soul");
      map.set (SOUL_ID, "gospel");

      /*techno*/
      map.set (TECHNO_ID, "techno");
      map.set (TECHNO_ID, "minimal");
      map.set (TECHNO_ID, "trance");
      map.set (TECHNO_ID, "chillout");
      map.set (TECHNO_ID, "electronic");
      map.set (TECHNO_ID, "electronica");

      /*other*/
      map.set (OTHER_ID, "other");
      map.set (OTHER_ID, "african");
      map.set (OTHER_ID, "alternative");
      map.set (OTHER_ID, "ambient");
      map.set (OTHER_ID, "asian");
      map.set (OTHER_ID, "brazilian");


```

Seems to some common  excluded & myself have no clue what 'house' is..

---

### Post by Framli on 2012-03-24
Could you please file a bug for the missing album art? Thanks!

---

### Post by x-shaney-x on 2012-03-24
Does anyone know if the album art is displaying when using banshee rather than rhythmbox?

---

### Post by Framli on 2012-03-24
Yes, Banshee album art works in the Music lens. And if you are a Banshee -> Rhythmbox switcher, most of your albumart from Banshee will be re-used for Rhythmbox in the Music lens.

Currently, if you use Rb and don't have album art in the music lens: install Banshee, let it find album art for your library, then remove it :D

A fix is on its way and should land soon after Beta 2.

---

### Post by x-shaney-x on 2012-04-12
> **Framli said:**
> A fix is on its way and should land soon after Beta 2.

I noticed the music lens was updated today and still no album art, though it DOES show in the stuff available for purchase of course.

---

### Post by shadowfirebird on 2012-04-12
The music lens doesn't work for me because I use Clementine. 

The "envelope icon" doesn't show my tweets because I don't use Gwibber.

Nor does it show my IMs, because I don't get along with Empathy.

A little OT, I know -- but for me this is the most annoying aspect of Unity.  It makes assumptions which the user cannot correct.

---

### Post by mc4man on 2012-04-12
> **x-shaney-x said:**
> I noticed the music lens was updated today and still no album art, though it DOES show in the stuff available for purchase of course.

Here's one bug on, it's was left for dead so just re-confirmed
Whether there is another active bug on or any plans to fix, ect. don't know.
Atm the only way to get album art into the lens is to install banshee. Then it will add the art which will become available in the RB part of the lens

[https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/965483](https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/965483)

---

### Post by x-shaney-x on 2012-04-12
> **shadowfirebird said:**
> A little OT, I know -- but for me this is the most annoying aspect of Unity.  It makes assumptions which the user cannot correct.

I must agree this was one of the bigger concerns of mine from the early days of the messaging menu and onwards through unity features.

If you don't use default apps, unity starts to make less and less sense.

---

### Post by mc4man on 2012-04-12
It's possible a Clementine scope will become available after 12.04 release, if so likely to be seen here
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/839319](https://bugs.launchpad.net/ubuntu/+source/unity-lens-music/+bug/839319)

---

### Post by shadowfirebird on 2012-04-12
> **x-shaney-x said:**
> If you don't use default apps, unity starts to make less and less sense.

To my mind this is merely a matter of the lack of configuration options in Unity; my only concern is that the devlopers will stop adding *necessary* configuration options too soon.

There seems to be a rash of the "take it or leave it" POV in interface design recently, even in Linux, where you would have thought it was contra-indicated.

---

### Post by mc4man on 2012-04-13
active bug on album art in lens for RB, may not show till SRU1
[https://bugs.launchpad.net/unity-lens-music/+bug/976067](https://bugs.launchpad.net/unity-lens-music/+bug/976067)

---

### Post by x-shaney-x on 2012-04-13
Sru 1?

---

### Post by mc4man on 2012-04-13
> **x-shaney-x said:**
> Sru 1?

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

