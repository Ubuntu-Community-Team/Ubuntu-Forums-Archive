---
title: "Whats opensource equiv of flash?"
date: 2009-05-21
forum: Ubuntu Studio
---

### Post by kapi on 2009-05-21
was wondering what linux users/web developers use as an alternative to flash for developing multimedia sites

thanks

---

### Post by LoloftheRings on 2009-05-21
Gnash!

 Gnash SWF Viewer
Gnash is a free SWF movie player, which works either standalone, or as plugin for Firefox/Mozilla or Konqueror. Currently it is in a alpha state. The plugins are under heavy development at this time.  
Gnash supports the majority of Flash opcodes up to SWF version 7, and a wide sampling of ActionScript classes for SWF version 8.5. All the core ones are implemented, and many of the newer ones work, but may be missing some of their methods. Included in the Gnash is an XML based messaging system, as specified in the Flash specification. This lets a flash movie communicate over a TCP/IP socket, and parse the incoming XML message. This lets a movie be a remote control for other devices or applications. This package includes the standalone GTK+-based OpenGL player. Homepage: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

(from add/remove)

---

### Post by super breadfish on 2009-05-21
For Flash creation you there are few programs but none of them are really drop in replacements for Adobes tools.

You could give KToon and Ajax Animator a look.
[KToon]("http://ktoon.toonka.com/")
[Ajax Animator]("http://antimatter15.110mb.com/wp/?page_id=57")

IMO though, it's best to avoid Flash when possible.

---

### Post by kapi on 2009-05-21
Thanks,

I don't use flash, just had an interview the other day and the employer was looking for flash experience. I don't have any and the guy was a pratt, I told him that flash is a pain and real slow and can also put off alot of internet users.

I do know about synfig whick I suppose could fall into the same arena

Kapi

---

### Post by kapi on 2009-05-29
Am trying in vain to get position as a web developer, However i was informed that I need to develop my flash skills. problem is I moved to Ubuntu 6 months ago and now have no way to use flash. Is there an opensource application that does the same as flash?

I'm sure I'm not the only person who has come across this dilema

kapi

---

### Post by Stochastic on 2009-05-29
If you're trying to get a position with a web design company then you'll need to buy some Adobe software (it may run in Wine, but you may need a Virtual windoze or mac install).  If you're trying to make a name for yourself as a web developer for contract work, you can totally avoid flash.

There are a few interesting developments for animation work over the web.  First I'd say take a peek into HaXe [http://haxe.org/](http://haxe.org/) (it can do actionscript work).  Then, on the horizon (not for some time will firefox support land) is SMIL animation for SVG graphics (unfortunately IE still doesn't like SVG graphics, but Opera already has about 97% of the SMIL standard implemented in their SVG support).

There's also Flash4Linux (or is it F4L) which is aiming to be a flash authoring program on Linux, but I haven't had much success with that.

You can also throw some fancy CSS, javascript, and animated gifs together to get many features that the average Flash developer makes.  In the end, I've grown a major distaste for Flash (other than some media delivery methods such as Youtube) most of it is just annoying, poorly designed, and inaccessible according to W3C accessibility standards.

---

### Post by kapi on 2009-05-29
Thanks for replying, while searching I have come across a few links, one is this page

[http://osflash.org/open_source_flash_projects#command_line_tools_compilers_etc](http://osflash.org/open_source_flash_projects#command_line_tools_compilers_etc)

this holds quite a few opensource alternatives to flash

the other is 

[http://www.openlaszlo.org](http://www.openlaszlo.org)

this seems to have been adopted or sponsored by sun, will delve further but am impressed with what I've seen so far. As for SMIL well while at uni we were made aware of the language but as you mentioned the lack of support seems to make it a non contender

Thanks again

---

### Post by bobince on 2009-05-29
The sad fact is that if you're asked to “improve your Flash skills” they probably mean exactly that: they require competence with a particular application, rather than the underlying technology. There are other ways to produce Flash content, and alternatives to Flash content, but if you're getting a job in a Flash shop you'll need to know Flash.

I grit my teeth and run it in an XP Virtualbox when I have to.

---

### Post by johnh10000 on 2009-07-11
I am trying to put some fancy graphics on my website.

I'm considering actionscript, but would like a nice gui, type thingy.
Also considering java, as I'm a bit rusty, but know c++, it looks similar.

Ok at the mo, I'm looking forward to Hallowen, and want some flying pointed hat creatures, and the like flying about.*

Also I want some game, hhhmm ones I've written.

*could java do this?

any ideas welcome.

tux.isa-geek.org

---

### Post by LoloftheRings on 2009-07-12
You could try HTML5's ogg theora support!
However, it's just firefox (pretty big market share though) that can handle it.

---

### Post by bobince on 2009-07-17
> **johnh10000 said:**
> I am trying to put some fancy graphics on my website.

In what way ‘fancy’?

You can certainly move 2D graphics around the page using plain old JavaScript, and there are any number of pre-made JavaScripts you can steal that will fly a bunch of images about the page (though be aware most people find this quite irritating).

Java applets only take over a rectangle on the page, you couldn't use an applet to overlay graphics onto functioning HTML. You'd have to make the whole site Java (which would be a really bad idea for accessibility, usability and SEO).

---

### Post by johnh10000 on 2009-07-17
> **bobince said:**
> In what way ‘fancy’?

You can certainly move 2D graphics around the page using plain old JavaScript, and there are any number of pre-made JavaScripts you can steal that will fly a bunch of images about the page (though be aware most people find this quite irritating).

hmmm too late.  I realise that, take a look at hhmm "my" aircraft on aboutme page.

Java applets only take over a rectangle on the page, you couldn't use an applet to overlay graphics onto functioning HTML. You'd have to make the whole site Java (which would be a really bad idea for accessibility, usability and SEO).

I've realised now, I can do basicly what I want with JS or when I get around to learning it, Java.

Thanks for the info though

tux.isa-geek.org.
Saying that the only stuff that isn't on my site is asp, perl and java

---

