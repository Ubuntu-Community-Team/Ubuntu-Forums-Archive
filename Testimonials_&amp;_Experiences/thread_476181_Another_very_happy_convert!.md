---
title: "Another very happy convert!"
date: 2007-06-16
forum: Testimonials &amp; Experiences
---

### Post by schwank on 2007-06-16
Just wanted to make a post to commend the ubuntu team for making an excellent easy to use distribution.

I am a professional software developer using Windows and .Net but I have grown increasingly weary of the many issues I encounter every day in my work, and I do not like the positions Microsoft takes on many issues in the computing world. I build tons of machines from scratch and manage much of my companies software and hardware needs.

I have installed (at least attempted) various flavors of linux (and BeOS) at various times over the last many  years. But I never found it easy enough to stick with. I loved Be actually but we know how that went. Regardless, I picked up a disc of Feisty somewhere, and tossed it into an older Dell 600m laptop. The desktop experience was quite pleasant and most of the basics worked right away. So I clicked Install...

Here I am a couple weeks later. I honestly find it a chore to use windows and visual studio and such now. Almost everything I needed was there right away. OpenOffice. Evolution. Firefox. The B wireless and all networking (even smb bless you!), audio, and graphics handled themselves.The autoupdating utility found a bunch of patches and got me up to date on all my libraries. I got H.264 working with minimal effort. I have now gone the extra steps of installing Monodevelop, Eclipse, Screem and more development tools and look forward to digging in.

Anyway, I raise my mug in a hearty toast to the Ubuntu developers! Thanks for finally making linux 'ready for the desktop'. You have won another convert from the Windows world. I would say that you are not a Windows alternative... you have them beat hands down! I will definitely be converting my other machines over as time permits.

:KS

---

### Post by wolfen69 on 2007-06-16
welcome aboard!!

---

### Post by Geekkit on 2007-06-17
Welcome to the other side, and yes those Ubuntu developers are great people aren't they? Since you're into software development I'll pass on some of my experience in the hopes that it is useful ...

Since you're a .NET developer, you'll probably be interested in Mono ( [http://www.mono-project.com](http://www.mono-project.com) ). I personally haven't used it for quite a while but from what I've read about it, there seems to be a lot of progress and it's matured quite a bit in the last year. They even have what looks to be quite a spiffy development tool called MonoDevelop ([http://monodevelop.com/Main_Page](http://monodevelop.com/Main_Page) ) which looks promising although I haven't used it so I can't comment on its abilities.

I don't know if you do Java/C/C++ but if you do you'll definitely be interested in Netbeans. Netbeans for me was one of those development tools that annoyed me at the beginning because of it's plethora of options and such. Then one day I downloaded the Mobility pack and realized how powerful it was. I became hooked. Netbeans ( [http://www.netbeans.org/](http://www.netbeans.org/) ) now has the following packs for development:

[LIST]
[*]Mobility for J2ME (Java for mobile devices, J2ME profiler, obfuscator)
[*]Visual Web (drag-n-drop for Web pages including a CSS editor)
[*]Enterprise (UML modeling tools that reverse and forward engineer, XML Schema editing)
[*]Profiler (check for memory leaks, etc.)
[*]C/C++ (interesting, you can now do C/C++ in Netbeans)
[/LIST]

As for installation, here's what worked for me:

1.) Go into Synaptic and remove all the other JVMs. Unless for some strange reason you need Java 1.4, 1.5. It's easier to go to Sun's Web site, grab the download bin, right click on the icon, and allow for it to be executed. Alternatively you can simply go to the command prompt and type: sudo chmod u+x java---1.6----.bin. then type sudo ./java---1.6----.bin and you'll be off to the races.

Next, download Netbeans and all the packs from the Netbeans site and do the same thing (give them execution rights and run them. If you've ever installed Java on Windows, you'll find this install to be painless and quick since there's no diddling of the registry. The longest you wait is the download.

What I do is if I'm writing quick little programs in whatever language, I use GEdit since it fires up real quick. It has code coloring and recognition for more languages/scripting languages/markup syntaxes that you can shake a stick at. GEdit is my EditPlus replacement since that's what I used for literally seven years. Netbeans will feel much like VS with all the features.

If you're into C programming and you want to create some GUIs then you'll want to check out GLADE ( [http://glade.gnome.org/](http://glade.gnome.org/) ). GLADE is a drag and drop tool for creating GUIs in GTK+ for Gnome. It's not bad and stores its files in XML. Version 2 outputs C code although version 3 threatens to no longer allow C output and simply use LibGlade which is similar to using XAML in .NET - the library uses the XML file at runtime to generate the GUI. Glade can be had by using Synaptic.

GTK+ programming is all C based although there is a wrapper in C++ if you feel absolutely repulsed by the idea of doing GUI programming in C. At first my response to doing GUI programming in C was "Ewww." But after studying the APIs and using GLADE, I didn't find it that bad. They make quite a few macros, and they heavily make use of structs/typedefs which try to sugar code the whole experience so it really winds up feeling OO-ish. It's actually quite cool. I'm sure someone will point out the KDE route as well. For me I'm sticking with Gnome since its the desktop environment for the main Ubuntu distro, Free BSD, and for Solaris OS so I figure if I need to code for those other Unix flavors GTK+ will be knowledge that I can reuse.

You'll need to go to Synaptic and download libgtk which will grab all its dependencies. I'm about to explore the Cairo portion of GTK+ which allows for some really funky drawing of custom GUI components. That's about it from me. Hopefully something useful in this long reply.

Welcome to Ubuntu!

---

### Post by Raffaele Recalcati on 2007-06-27
I've been working during last 4 year in linux embedded development.
I used usually Redhat and then Fedora distros.

Some weeks ago I download your Feisty 7.04 distro.
First of all, apt-get is much better than yum, but the most important thing is that ubuntu doesn't any effort to be installed.
In my work is important because I use linux as a platform for the arm embedded, and I don't develop x86.

So thank you very much, 
I'll be very glad to contribute in some way.

---

### Post by weblordpepe on 2007-06-28
Wow thats really exciting seeing some pro developers come to the dark side. I bet you guys have noticed by now the development packages don't cost an arm & a leg? :)

---

