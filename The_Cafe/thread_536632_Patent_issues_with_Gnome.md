---
title: "Patent issues with Gnome?"
date: 2007-08-27
forum: The Cafe
---

### Post by kirios on 2007-08-27
[COLOR="DarkRed"]Is it possible that Gnome may have patent issues because of Beagle, F-spot and other Gnome apps that use Mono? The FAQ on the Mono website isn't very easy to interpret.[/COLOR]

[http://fsfeurope.org/documents/rms-fs-2006-03-09.en.html#q1]("http://fsfeurope.org/documents/rms-fs-2006-03-09.en.html#q1")
> Richard Stallman: Mono is a free implementation of Microsoft's language C#. Microsoft has declared itself our enemy and we know that Microsoft is getting patents on some features of C#. So I think it's dangerous to use C#, and it may be dangerous to use Mono. There's nothing wrong with Mono. Mono is a free implementation of a language that users use. It's good to provide free implementations. We should have free implementations of every language. But, depending on it is dangerous, and we better not do that.

[http://www.mono-project.com/FAQ:_Licensing#Could_patents_be_used_to_completely_disable_Mono.3F]("http://www.mono-project.com/FAQ:_Licensing#Could_patents_be_used_to_completely_disable_Mono.3F")
> For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

---

### Post by Andrewie on 2007-08-28
When I want balanced information the last person I turn to is Richard Stallman. Red Hat appears is fine with mono so I don't think there are any issues to worry about.

---

### Post by kirios on 2007-09-13
> **Andrewie said:**
> When I want balanced information the last person I turn to is Richard Stallman. Red Hat appears is fine with mono so I don't think there are any issues to worry about. 
[COLOR="DarkRed"]Have a look at this (current) thread on FedoraForum: [/COLOR]
[http://forums.fedoraforum.org/forum/showthread.php?t=165708]("http://forums.fedoraforum.org/forum/showthread.php?t=165708")

[COLOR="DarkRed"]Btw I think Fedora includes mono but Red Hat has left it out of RHEL.[/COLOR]

---

### Post by ryno519 on 2007-09-13
Usually a fan of RMS, but...

[http://www.gnu.org/software/dotgnu/](http://www.gnu.org/software/dotgnu/)

WTF!?

---

### Post by 23meg on 2007-09-13
What's your problem with DotGNU?

---

### Post by Anthem on 2007-09-13
> **23meg said:**
> What's your problem with DotGNU?
Other than the fact that it's nowhere near as good as Mono?

How about the fact that everything Stallman says against Mono could also be said against dotGNU?

---

### Post by 23meg on 2007-09-13
[QUOTE=Anthem]How about the fact that everything Stallman says against Mono could also be said against dotGNU?[/QUOTE]

How, and why?

---

### Post by Anthem on 2007-09-13
> **23meg said:**
> How, and why?
Well, first he says "Mono is a free implementation of Microsoft's language C#. Microsoft has declared itself our enemy and we know that Microsoft is getting patents on some features of C#. **So I think it's dangerous to use C#, and it may be dangerous to use Mono**."

But why would dotGNU be any less dangerous?
> The DotGNU project aims to be for webservices and for C# programs what GNU/Linux is rapidly becoming for desktop and server applications: the industry leader and provider of Free Software solutions.

DotGNU currently consists of three main development projects (further components will be added over time):

[list][*] DotGNU Portable.NET, an implementation of the Common Language Infrastructure (CLI), more commonly known as ".NET", includes everything that you need to compile and run C# and C applications that use the base class libraries, XML, and Systems.Windows.Forms. Currently supported CPUs: x86, ppc, arm, parisc, s390, ia64, alpha, mips, sparc. Supported operating systems: GNU/Linux (on PCs, Sparc, iPAQ, Sharp Zaurus, PlayStation 2, Xbox,...), *BSD, Cygwin/Mingw32, Mac OS X, Solaris, AIX.
[*]phpGroupWare, a multi-user web-based GroupWare suite, which also serves to provide a good collection of webservice components, all of which can be accessed through XML-RPC so that you can easily integrate them into webservice applications of your own.
[*]The DGEE webservice server is also moving forward nicely.[/list]

---

### Post by 23meg on 2007-09-13
Some differences are highlighted in the articles below:

[http://www.internetnews.com/dev-news/article.php/3361991](http://www.internetnews.com/dev-news/article.php/3361991)
[http://en.wikipedia.org/wiki/DotGNU](http://en.wikipedia.org/wiki/DotGNU)

---

### Post by vexorian on 2007-09-13
> **Anthem said:**
> Other than the fact that it's nowhere near as good as Mono?

How about the fact that everything Stallman says against Mono could also be said against dotGNU?
MS is waiting .net to become mandatory and then they will begin the attack, they will request every Linux user to pay a Linux tax or they will sue for using Mono.

[http://www.novell.com/linux/microsoft/openletter.html](http://www.novell.com/linux/microsoft/openletter.html)
> Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice as well as .NET and Windows Server.

if Mono  was a non-issue Microsoft wouldn't publicly announce customers need "coverage" for it. Of course they also give coverage for Samba and OpenOffice.org (...those bastards...)  but the thing is that MS is right now actively "collaborating" with the Mono project, or letting patented code into it. At the end it will not matter how true or false microsoft's assertions are, it will be your lawyers vs. MS' .

The good news is that gnome, at least right now is not dependant on Mono, we can remove beagle, and tomboy is useless anyways. Instead of beagle perhaps google desktop works? although my memory is not sure they made one for Linux. Even though the gnome founder is a total MS sell out, gnome might have some hope. At least Icaza has denied he plans to make the hole gnome Mono dependant.

---

