---
title: "another reason why NOT windows"
date: 2005-08-12
forum: The Cafe
---

### Post by student on 2005-08-12
another reason for those asking why to leave windows...

[quote="http://www.sysinternals.com/Information/TipsAndTrivia.html#HiddenKeys"]

Hidden Registry Keys?

A subtle but significant difference between the Win32 API and the Native API (see Inside the Native API for more information on this largely undocumented interface) is the way that names are described. In the Win32 API strings are interpreted as NULL-terminated ANSI (8-bit) or wide character (16-bit) strings. In the Native API names are counted Unicode (16-bit) strings. While this distinction is usually not important, it leaves open an interesting situation: there is a class of names that can be referenced using the Native API, but that cannot be described using the Win32 API.

How is this possible? The answer is that a name which is a counted Unicode string can explicitly include NULL characters (0) as part of the name. For example, "Key\0". To include the NULL at the end the length of the Unicode string is specified as 4. There is absolutely no way to specify this name using the Win32 API since if "Key\0" is passed as a name, the API will determine that the name is "Key" (3 characters in length) because the "\0" indicates the end of the name.

When a key (or any other object with a name such as a named Event, Semaphore or Mutex) is created with such a name any applications using the Win32 API will be unable to open the name, even though they might seem to see it. The program below, RegHide(source code is included), illustrates this point. It creates a key called "HKEY_LOCAL_MACHINE\Software\Sysinternals\Can't touch me!\0" using the Native API, and inside this key it creates a value. Then the program pauses to give you an opportunity to see if you can view the value using any Registry editor you have handy (Regedit, Regedt32 or a third-party Registry editor). Because Regedit and Regedt32 (and likely an third party Registry editor) use the Win32 API, they will see the key listed as a child of Sysinternals, but when you try to open the key you'll get an error. This is because the Registry editor will try to open "Can't touch me!" without the trailing NULL (which is interpreted as the end of the string) and won't find this name. After you've verified this exit the program and this special key will be deleted. [/quote]

---

### Post by KingBahamut on 2005-08-12
Mark Rossinovich hard at work. 

That guy blows my mind at times......

---

### Post by Kyral on 2005-08-12
What does this mean again?

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=Kyral]What does this mean again?[/QUOTE]


+++++++++ - new info from this thread

OOOOOOOO - my head

---

### Post by KingBahamut on 2005-08-12
Plain and simple truth.......

Microsoft must ditch the Registry.....without question.

---

### Post by Lord Illidan on 2005-08-12
Ok, so after that piece of technobabble, why exactly should I not use Windows? I would understand if the thread was about some patents or microsoft suing, but not this..The title is inappropriate...and the content....undecipherable...

No offence to you, student, but use titles more appropriately? Or else, can someone explain what this means?

---

### Post by student on 2005-08-12
[QUOTE=Lord Illidan]can someone explain what this means?[/QUOTE]

in programming, a string (sentance) is actually a table of characters. The sentance always ends with '\0' because doing it this way, it's a lot easier to work with the tables, without the need to check the length of each string.

In windows you can make a registy key with the actual name ending with '\0', using a lower level kernel function. This means that when you try to get the key using a "normal" function, you are returned an error, not found, because the function thinks the string ends earlier, and thus does not find the key it seeks.

more or less I think...

---

### Post by Lord Illidan on 2005-08-12
Sorry... still not understanding.. I know what a string is, I have used Pascal and C++, but the registry... is beyond my understanding, lol...

---

### Post by KingBahamut on 2005-08-12
Hey, Its not a Bug...Its a Feature... =)

---

### Post by KiwiNZ on 2005-08-12
What I understand here is and I will use a few less words that the quote has .

The Windows registry is poo

---

### Post by student on 2005-08-12
[QUOTE=Lord Illidan]Sorry... still not understanding.. I know what a string is, I have used Pascal and C++, but the registry... is beyond my understanding, lol...[/QUOTE]

[http://www.winguides.com/registry/showcase.php](http://www.winguides.com/registry/showcase.php)

[quote="some irish dude"]
The Windows Registry

Now, on the face of it, this may seem like a good idea, however, as
any developer will tell you, they only use it because the commands are
quick, simple and, when it comes down to it, security is mainly the
end-users responsibility.

It would be much faster, simpler and provide greater system security
to use an ini file. Linux uses this approach with config files. An
entire database must be examined each time request is made. This is
why Windows slows down after you begin installing applications. The
registry grows and more cycles must be dedicated to completing each
query.

When you multiply this, by the wide range of systems accessing the
registry, it is clear to see, that as a design architecture, it is
completely moronic.

That is, until it is examined from another perspective, try the
following perspectives as examples:

a. HKEY_CURRENT_USER - psychological profile of logged on user,
real-time usage focus.

b. HKEY_LOCAL_MACHINE - Detailed reporting of hardware and a wide
range of traceable unique identifiers

c. HKEY_USERS - psychological profiling of all users, post-forensic usage focus.

d. HKEY_CURRENT_CONFIG - Advanced psychological profiling based on a
ranking system of 'psychologically-based options' embedded throughout
the system. This could include things like favorite colour, pictures,
sounds, etc.

Throughout the registry are an extensive amount of MRUs. These areas
store your recently accessed documents each application and other
information. Now instead of having a single area were these are
stored, for both rapid access and cleaning purposes, Windows was
designed to fragment these throughout the registry database.

Firstly, this makes cleaning the registry a specialized job, as a
mistake can corrupt Windows. Secondly, and most importantly, this is
what we call 'fragmentation'.

Now 'fragmentation' is a well known source of problems when accessing
information. Many will point out, that the registry is a hierarchy and
that that this eliminates fragmentation. I must point out that I am
referring to the 'entire structure of recorded information' and not
the technical definition of fragments of data.

By fragmenting the various forms of 'recorded information' throughout
the registry, it can take upwards of a week to list every key that
should be cleaned. The entire process must be repeated each time a new
application is installed, to determine what exactly was placed into
the registry. Windows also uses an extensive amount of MRUs that have
been altered to an 'unreadable' format. This would leave 95% of users
completely unaware of Microsoft was recording.

There is no need or requirement for a registry, other than to provide
central access to 'private information'. As a programming architecture
model, the design borders on the moronic and is directly opposing
every known, best practice, in programming.

The true motivations behind the registry design are quite clear and
highly specific.

Done by design.[/quote]

---

### Post by wmcbrine on 2005-08-13
My summary:

Secret stuff in the registry that can't be removed.

---

