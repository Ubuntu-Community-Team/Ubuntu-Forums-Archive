---
title: "Are there any apps to convert units?"
date: 2008-02-19
forum: The Cafe
---

### Post by figure9 on 2008-02-19
Is there a units conversion application for ubuntu? Basically a program that will convert a clumsy unit like kilometers per hour a useful unit like furlongs per fortnight?

---

### Post by Fbot1 on 2008-02-19
[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search)

---

### Post by bruce89 on 2008-02-19
> **Fbot1 said:**
> [http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search)

In other words, search google for things like "1 foot in centimetres" etc.

Furlongs per fortnight sounds very clumsy.

---

### Post by ~LoKe on 2008-02-19
> **Fbot1 said:**
> [http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search)

Google is not an application.

---

### Post by Fbot1 on 2008-02-19
> **~LoKe said:**
> Google is not an application.

but web browsers are

---

### Post by bruce89 on 2008-02-19
> **~LoKe said:**
> Google is not an application.

Fine, try this:

[PHP]
#include <stdio.h>

enum
{
	INCH_TO_CM = 1,
	POUND_TO_KG = 2,
	FOOT_TO_M = 3
} mode;

int
main (void)
{
	int mode;
	double imperial;
	double metric;

	printf ("Choose from the menu\n");
	printf ("1 -- Inches to centimetres converter\n");
	printf ("2 -- Pounds to kilograms converter\n");
	printf ("3 -- Feet to metres converter\n");
	scanf ("%d", &mode);

	switch (mode)
	{
		case INCH_TO_CM:
			/* Program 1 */
			printf ("Enter inch value ");
			scanf ("%lf", &imperial);
			metric = imperial * 2.54;
			printf ("%lf\n", metric);
			break;
		case POUND_TO_KG:
			/* Program 2 */
			printf ("Enter pounds value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.4535924;
			printf ("%lf\n", metric);
			break;
		case FOOT_TO_M:
			/* Program 2 */
			printf ("Enter feet value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.3048;
			printf ("%lf\n", metric);
			break;
		default:
			fprintf (stderr, "Mode not recognised\n");
	}
	return 0;
}
[/PHP]

```
gcc -g -Wall -o conv conv.c
```

---

### Post by JonUK76 on 2008-02-19
Yes, add the ConvertAll program through Add/Remove programs. Works for me :)

---

### Post by Fbot1 on 2008-02-19
> **bruce89 said:**
> Fine, try this:

[PHP]
#include <stdio.h>

enum
{
	INCH_TO_CM = 1,
	POUND_TO_KG = 2,
	FOOT_TO_M = 3
} mode;

int
main (void)
{
	int mode;
	double imperial;
	double metric;

	printf ("Choose from the menu\n");
	printf ("1 -- Inches to centimetres converter\n");
	printf ("2 -- Pounds to kilograms converter\n");
	printf ("3 -- Feet to metres converter\n");
	scanf ("%d", &mode);

	switch (mode)
	{
		case INCH_TO_CM:
			/* Program 1 */
			printf ("Enter inch value ");
			scanf ("%lf", &imperial);
			metric = imperial * 2.54;
			printf ("%lf\n", metric);
			break;
		case POUND_TO_KG:
			/* Program 2 */
			printf ("Enter pounds value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.4535924;
			printf ("%lf\n", metric);
			break;
		case FOOT_TO_M:
			/* Program 2 */
			printf ("Enter feet value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.3048;
			printf ("%lf\n", metric);
			break;
		default:
			fprintf (stderr, "Mode not recognised\n");
	}
	return 0;
}
[/PHP]
```
gcc -g -Wall -o conv conv.c
```

Lol, wouldn't it be a whole lot easier to just use multiplication and division.

---

### Post by mikelygee on 2008-02-19
As a command-line sort of guy, I use "units":

[INDENT][FONT="Courier New"]$ units
1989 units, 71 prefixes, 32 nonlinear units

You have: kilometres per hour
You want: furlongs per fortnight
        * 1670.2424
        / 0.00059871548
You have:
^D[/FONT][/INDENT]

or simply:
[INDENT][FONT="Courier New"]$ units "kilometres per hour" "furlongs per fortnight"
        * 1670.2424
        / 0.00059871548
[/FONT][/INDENT]

---

### Post by quanumphaze on 2008-02-19
Try "Qalculate!"
It's an advanced calculator with a conversion feature.

Find it in Add/Remove

---

### Post by Vadi on 2008-02-19
Qualculate does everything.

---

### Post by sobakasu on 2008-04-03
Or try **convertall**. It's in the repos but I haven't yet tried it personally.
It's a QT app, though -- does anybody know if there's a GTK alternative? Under Windows, I loved [Abby]("http://www.sheepfriends.com/?page=abby"). I don't know, there might be something as simple for Linux without the need for using WINE?

---

### Post by swordsearcher on 2008-04-06
Here is one....


[  Quad-Lock Unit Converter]("http://www.swordwarrior.net/UnitConverter.html")

---

### Post by HermanAB on 2008-04-06
The program 'units' is pretty good:

$ units
2439 units, 71 prefixes, 33 nonlinear units

You have: 12 liters per hundred kilometers
You want: miles per hogshead
        reciprocal conversion
        * 1234.8766
        / 0.00080979754

You have: 160 kilometers per hour
You want: furlong per fortnight
        * 267239.32
        / 3.7419643e-06

The * is the answer you want, the / is the reciprocal, which is sometimes useful.

Cheers,

Herman

---

### Post by adamklempner on 2008-04-06
I know it is not a stand alone app, but:

[http://www.onlineconversion.com/](http://www.onlineconversion.com/)

does pretty much everything I have ever thrown at it.  And I am an engineer who has worked with some very odd units...

---

### Post by Iandefor on 2008-04-06
I'll have to give another shoutout to units. It handled kilometers per hour to furlongs per fortnight without a hitch:

```
ian@leviathan:~$ units "1 kilometer per hour" "furlongs per fortnight"
    * 1670.2458
    / 0.00059871429
```It's also good enough to tell me the speed of light in a vacuum in stadia per month in the Islamic calendar:
```
ian@leviathan:~$ units -t "299792458 meters per second" "stadia per islamicmonth"
4.1303298e+12
```

---

### Post by shrinux on 2008-11-18
> **JonUK76 said:**
> Yes, add the ConvertAll program through Add/Remove programs. Works for me :)
Thanks man :-)

---

### Post by bobbocanfly on 2008-11-18
Google uses GNU "units" (the command everyone is telling you about). I watched a talk where someone (Benjamin Mako Hill?) typed in a phrase that bugged out in GNU Units, and got the exact same output from Google.

---

### Post by mips on 2008-11-18
> **figure9 said:**
> Basically a program that will convert a clumsy unit like kilometers per hour a useful unit like furlongs per fortnight?

Why, did you invent a time machine?

---

### Post by forrestcupp on 2008-11-18
> **~LoKe said:**
> Google is not an application.

Google absolutely *is* an application.  Google actually encompasses several applications.  Their apps just happen to use a web browser as their vehicle.  There's a reason they call one set of their applications "Google Apps".

If you've ever programmed a web app using PHP or any one of many other web languages, you probably wouldn't appreciate it if someone said it's not an application. ;)

But I'm willing to concede that a web page created with simple html is *not* and app.

---

### Post by daverich on 2008-11-18
I like using google ,- it'll do currency conversion too.

Kind regards

Dave Rich

---

### Post by Mr. Picklesworth on 2008-11-18
Gourmet does unit conversions if you ever need to do food stuff. It even handles densities in some cases. Really handy with butter, for example.
Otherwise, Qalculate is indeed the way to go,

---

### Post by Paqman on 2009-08-10
There's a great app called "elementary arithmetic" that can do this for you ;)

---

### Post by Osmodivs on 2011-10-04
> **Fbot1 said:**
> [http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=bJd&q=1+foot+in+microns&btnG=Search")

He asked for "*applications* in _**UBUNTU**_".    
                  :x

---

### Post by sffvba[e0rt on 2011-10-05
Back to sleep thread...


404

---

