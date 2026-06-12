---
title: "Pigs fly, Mono in Fedora"
date: 2006-01-10
forum: The Cafe
---

### Post by Lovechild on 2006-01-10
It looks like the legal issues Fedora had with Mono have been resolved, at least as of today Fedora Development ships with Mono.

My prayers have been answered..

[http://www.0xdeadbeef.com/?p=159](http://www.0xdeadbeef.com/?p=159)

---

### Post by tom-ubuntu on 2006-01-10
Very good move from Fedora; .Net/C# is an excellent Framework and development language. With the right tools we will see a lot of nice applications soon.

---

### Post by Lovechild on 2006-01-10
This I suppose also opens up for inclusion of Mono apps in GNOME, no major distributor (excluding Sun) has a negative stance on Mono anymore. 

And yes Mono is indeed an excellent framework.

---

### Post by ember on 2006-01-10
Well - as far as I know, there are no legal issues as long as you stick to the ECMA-standardized parts of Mono/.Net (i.e. basically you use GTK# instead of Windows.Forms and you do not use the ADO-database layer).

I'm very happy that Mono is finally in FC - maybe i'll give FC 5 a try.

---

### Post by tom-ubuntu on 2006-01-10
[QUOTE=ember]Well - as far as I know, there are no legal issues as long as you stick to the ECMA-standardized parts of Mono/.Net (i.e. basically you use GTK# instead of Windows.Forms and you do not use the ADO-database layer).[/QUOTE]
That's exactly how I understood it aswell. 

Just out of interest and without studying the mono docs: what do you need to use instead of ADO? Someone know?

---

### Post by asimon on 2006-01-10
No wonder they never told us any details about those legal issues which prevented them to include Mono.

---

### Post by ember on 2006-01-10
[QUOTE=joeuser]That's exactly how I understood it aswell. 

Just out of interest and without studying the mono docs: what do you need to use instead of ADO? Someone know?[/QUOTE]

Sadly there is no way I know of (yet I am not the absolute Mono/.Net expert). But I'm not sure whether the Mono ADO object maybe perfectly legal when used as an abstraction layer for MySQL/PostgreSQL.

---

### Post by tom-ubuntu on 2006-01-11
Any word if Ubuntu will integrate mono aswell? Would be very cool to have beagle in Dapper :)

---

### Post by Lovechild on 2006-01-11
[QUOTE=asimon]No wonder they never told us any details about those legal issues which prevented them to include Mono.[/QUOTE]

Actually they did, it was a licensing issue pretaining to the GPL I think, linking gpl'ed applications to Mono would violate any potential patents in Mono as they would be required to be RANT-Royalty free. What is disturbing is that they didn't mention why it is suddenly now legal in the eyes of the RH lawyers, I didn't see anything about a change in that position.

I assume they just decided that currently no patents are being violated so as such Mono is safe for now.

Doing a net install of Rawhide today they already default to installing applications such as Beagle and f-spot.. quite decent.

---

### Post by curuxz on 2006-01-11
Isnt .net just an MS attempt to kill java, I know mono was suposed to address those issues but would someone please to explain to me why the .net platform is any better than java. I would be intrested since im not a programer of either (im  a web dev so I only know things like php)

---

### Post by Lovechild on 2006-01-11
[QUOTE=curuxz]Isnt .net just an MS attempt to kill java, I know mono was suposed to address those issues but would someone please to explain to me why the .net platform is any better than java. I would be intrested since im not a programer of either (im  a web dev so I only know things like php)[/QUOTE]

.NET is a fantatisc framework and C# is a wonderful language - I doubt it's just designed to kill java but it will because it's honestly just better and might I add ASP.NET is a wonderful web development tool.

---

### Post by curuxz on 2006-01-11
if asp.net is anything like asp then I doubt it will catch on, duno if there is a php.net. even if there was i think i would stay away from this monopoly tactic, is there any reason its good, i mean saying its great is fine but i was more asking why is it good? or why is it better? :)

---

### Post by ember on 2006-01-11
There is not PHP.Net (though I would be happy to see the PHP guys organize their libraries the way Microsoft did (and Java does, too) - I love PHP, but the library thing just sucks).
I guess, it's a matter of taste. I prefer C# to Java and at the moment PHP to C#. Though I am really thinking about switching my preferences.
And I found Visual Studio (2003) to be the best development enviroment, I ever used. Especially the debugger is really helpful (that is something that also doesn't work to well with standard php).

---

### Post by prizrak on 2006-01-11
The importance of .Net porting to Linux is the fact that it will be possible to run Windows apps on it natively. As more and more developers move towards .Net (since lets face it CPUs are fast enough to handle something like that w/o speed decreases) we will have more Windows apps running just fine on Linux w/o all the fun of tinkering with Wine/Crossover/Cedega, possibly allowing more people to move to Linux :)

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=joeuser]Any word if Ubuntu will integrate mono aswell? Would be very cool to have beagle in Dapper :)[/QUOTE]

Mono and all its applications are in the Ubuntu Repos.

Yet I hear its too much to fit Mono on the one install CD so it won't be part of the default install for a little while longer.

---

### Post by tom-ubuntu on 2006-01-12
[QUOTE=curuxz]if asp.net is anything like asp then I doubt it will catch on, duno if there is a php.net. even if there was i think i would stay away from this monopoly tactic, is there any reason its good, i mean saying its great is fine but i was more asking why is it good? or why is it better? :)[/QUOTE]
ASP and ASP.net are very different, the main differences: ASP was scrippted, mixed up with code and html, very unorganized. ASP.net is fully objectoriented, html and code is splitted, you have access to the whole .Net Framework.

Just the main difference. I haven't checked out ASP.net 2.0, which was release a short while ago. But they said something about saving around 70% of the code compared to ASP.net. If this is true, then you can develop websites really, really fast.

---

### Post by tom-ubuntu on 2006-01-12
[QUOTE=poofyhairguy]Mono and all its applications are in the Ubuntu Repos.

Yet I hear its too much to fit Mono on the one install CD so it won't be part of the default install for a little while longer.[/QUOTE]
Yeah, I know, i installed it. But I am talking about integrating mono by default into Ubuntu, like Fedora. Beagle would be a really great addiction for any desktop user using Ubuntu. And I am sure, there are many other great applications which would be of great use for a lot of people.

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=joeuser]Yeah, I know, i installed it. But I am talking about integrating mono by default into Ubuntu, like Fedora. Beagle would be a really great addiction for any desktop user using Ubuntu. And I am sure, there are many other great applications which would be of great use for a lot of people.[/QUOTE]

It might be on the DVD version. I don't know.

---

### Post by briancurtin on 2006-01-12
[QUOTE=joeuser]I haven't checked out ASP.net 2.0, which was release a short while ago. But they said something about saving around 70% of the code compared to ASP.net. If this is true, then you can develop websites really, really fast.[/QUOTE]
i have a bit of ASP.NET experience from a class, and it was pretty fast as it was to develop a pretty functional site. i would say it was "really fast" compared to the possible "really, really fast" of the newest version haha

---

### Post by Mr. Electric Wizard on 2006-01-19
Can someone tell me how up to date the Mono package in Apt is?
I have been reluctant to install it because I assume it is a really old version...
Can someone comment please?

The current version on [http://www.mono-project.com](http://www.mono-project.com) is 1.1.13

---

