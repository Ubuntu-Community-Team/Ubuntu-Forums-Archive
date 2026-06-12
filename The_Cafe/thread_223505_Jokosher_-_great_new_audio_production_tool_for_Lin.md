---
title: "Jokosher - great new audio production tool for Linux!"
date: 2006-07-26
forum: The Cafe
---

### Post by saracen on 2006-07-26
With it you can create and record music, podcasts and more, all from an integrated simple environment.  [This baby rocks!]("http://www.jokosher.org/")

---

### Post by blueturtl on 2006-07-26
Looks really nice. I will have to install it and see if it can outdo Audacity. Simple audio editing in Ubuntu is quite swell at the moment, but many hardcore audio enthusiasts complain over the lack of professional audio editing software. Maybe it too will change in the near future.

---

### Post by ComplexNumber on 2006-07-26
there's a problem it - some of the dependencies haven't even been released yet. therefore, some of the features have to be switched off when compiling.

---

### Post by philipacamaniac on 2006-07-31
It's first release doesn't even come close to Audacity in terms of functionality. But don't get me wrong, I really do think as they move along in development it will turn as the best Linux audio app. Maybe that will even start some healthy competition!

Jokosher 0.1, while a nice preview, has some serious issues:

- lacks volume fades
- lacks LADPSA effects, or any other types of effects
- has several gstreamer/gnonlin bugs related to clicking the track view repeatedly
- requires Gstreamer CVS to work

I made some comments on the Jokosher forum, and 0.2 should be leaps ahead with:

- LADSPA effects
- Python plugin architecture, possibly with Freesound plugin and sound clip plugin
- Working volume fades and crossfades
- Audio previews in the dialogue box
- Hopefully by that time Gstreamer will have released 0.10.9, and bugs will be squashed

On another note, their website design is awesome, and so is the seemingly strong willingness to work with the community as they develop the software. For the people, by the people... Viva la Jokosher!

---

### Post by HanZo on 2006-07-31
it's still a bit early in development... but the premises are good! the interface looks consistent and well designed (certainly miles ahead of audacity), the funztionality, once the project will advance will probably be very interesting.
True there is a lack of professional audio editing... but this is also connected to a lack of proper hardware support... yet there are some interesting projects in this field... like "Studio to go". although I could not test it since they have not released any demo or try out version... basically you have to buy it to try it...

oh.. there is one thing I don't really like about jokosher... the name... it's a bit difficult to memorize... and sounds a bit odd... but for the rest, thumbs up... and makes me want to participate!

edit: I just checked the "studio to go" site... they appear to have a demo for download...

---

### Post by saracen on 2006-07-31
and it's now in Edgy.  Just do a```
sudo aptitude install jokosher
```

---

### Post by saracen on 2006-07-31
[Jokosher]("http://www.jokosher.org/") is now in edgy. The 0.1 version was released recently and is still lacking some features, but they're on their way to making the best audio production tool for Linux. Just do a ```
sudo aptitude install jokosher
```

---

### Post by aanderse on 2006-07-31
this is great news, looks like an incredible too!

---

### Post by Andreas Isaksson on 2006-08-01
i've been waiting for this! i get the feeling it's as easy to use like acid for windows. this i must try =)

---

### Post by idn on 2006-08-01
This looks pretty sweet, good to see a innovitive new app thats not using mono - just my personal view tho :)

---

### Post by joselin on 2006-08-01
Looks great!

---

### Post by nalmeth on 2006-08-01
Wow,

This might push me over dapper

Thanks for the link up!

---

### Post by apoclypse on 2006-08-01
Nice. its done in python too. I'm working on a drum machine at the moment (trying to learn some python first). I think linux needs something like this. All that jack stuff i too complicated sometimes and only half of it works.

---

### Post by ubuntu_demon on 2006-08-01
> **nalmeth said:**
> Wow,

This might push me over dapper

Thanks for the link up!
It's in (heavy) development and therefor probably not very useful yet. Also it's not in Dapper. 

jokosher probably won't be backported to Dapper. Because :
- it needs python-central which isn't available in Dapper
- some functionality currently needs gstreamer 0.10.9 or higher while dapper has "0.10.6-0ubuntu2"
- some functionality currently needs gstreamer-gnonlin 0.10.4.2 (CVS) or 0.10.5 while Dapper has 0.10.4-0ubuntu1

---

### Post by ComplexNumber on 2006-08-01
>  - some functionality currently needs gstreamer 0.10.9 or higher while dapper has "0.10.6-0ubuntu2"
- some functionality currently needs gstreamer-gnonlin 0.10.4.2 (CVS) or 0.10.5 while Dapper has 0.10.4-0ubuntu1 thats why it will only work if the tarball (its actuallyy a python script) works, but with limited functionality at the moment until gstreamer 0.10.9 is released - the rpm doesn't work because the newest gstreamer in the fedora repos is gstreamer 0.10.8.

---

### Post by ubuntu_demon on 2006-08-01
> **ComplexNumber said:**
> thats why it will only work if the tarball (its actuallyy a python script) works, but with limited functionality at the moment until gstreamer 0.10.9 is released - the rpm doesn't work because the newest gstreamer in the fedora repos is gstreamer 0.10.8.
Edgy satisfies these dependencies :
- it has python-central
- it has libgstreamer0.10-0 Version: 0.10.9-1ubuntu1 
- it has gstreamer0.10-gnonlin Version: 0.10.5-1ubuntu1

---

### Post by jonobacon on 2006-08-26
Wow, thanks for all the incredibly kind words about Jokosher. It is really nice to see so much enthusiasm over it. :)

Now, to a few points. 0.1 was always intended as a preview release, and does indeed lack volume fades and other important features. But, we are currently hacking on 0.2, which is planned for release on 20th November 2006. We have already completed a bunch of new features:

 * support for LADSPA effects.
 * extension support, so third-party developers can write additional functionality that hooks into Jokosher. One such extension search the freesound site and allows you to easily drop sounds into a project with drag and drop. :)
 * instrument panning.
 * more instruments.
 * translations into a bunch of languages, all translated in Rosetta. :)
 * a new documentation site for collaborative community documentation.

In addition to this we are working on a stack of new features such as hooking up the volume fades, mixdown profiles, project templates and more.

We asre also building up a solid Jokosher community - see [http://www.jokosher.org/forums/](http://www.jokosher.org/forums/) for more.

Cheers,

  Jono

---

### Post by %hMa@?b&lt;C on 2006-08-26
audicity gets it done currently for me and my Telecaster.  Seems like I will give this proggy a run though.

---

### Post by banjobacon on 2006-08-26
With a planned release date of Nov. 20th, will Jokosher 0.2 be out in time for Edgy?

---

### Post by moitio on 2006-08-29
> **banjobacon said:**
> With a planned release date of Nov. 20th, will Jokosher 0.2 be out in time for Edgy?

No, probably not, so long as Edgy doesn't have a change of date. I'm sure some friendly developer will backport it :)

---

### Post by Rotarychainsaw on 2006-08-29
This is awesome!! I like audacity, but it gives me problems. If you can keep development going on this, it will be a real winner.

---

### Post by saracen on 2006-09-03
There's been an update on the status of Jokosher.  They've created some cool looking 'cairo-ified' dialog boxes.  [Check it out]("http://www.jonobacon.org/?p=753")

---

### Post by dswissmiss on 2006-10-27
Looks great! I just keep getting the "core dumped" segfault with no other errors so I don't really know how to fix it. Will keep an eye on it though.

---

