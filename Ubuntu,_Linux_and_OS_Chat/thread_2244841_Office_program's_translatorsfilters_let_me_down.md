---
title: "Office program's translators/filters let me down"
date: 2014-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by mastablasta on 2014-09-19
So I did a presentation for one of my customers and it included a few simple graphs. the presentation was done in MS Office 2013 Power point and I thought I could maybe present it on my Linux laptop. it uses custom company theme with certain pics for some backgrounds , a few graphs, a few animations and a few pics inserted on my own. it didn't work out. and I only saw the error when I was waiting in line for presentation. in the end I used a windows laptop from my colleague. I tried a few offices later on for fun to see how they will fare and the major issue were the graphs.

here is the original graph in MS office (nothing much just a single x and y axis): 
[img]http://shrani.si/f/14/Cs/NR6iHhE/msoffice2013.jpg[/img]

Libre office imported the document well. All animations were recognised, fonts got a suitable replacement and aside from an arrow I used in MS Office and didn't get the equivalent, theme got imported reasonably well, and I didn't have any major complaints. that is until I noticed this:
[img]http://shrani.si/f/3s/FH/27d4uZ3X/libreoffice.png[/img]

the dates were gone. ok I though it changed them into numbers and only needs the format set to "date & time". wrong - it was set to date format it just for some reason decided to have these numbers. I wonder how it managed to do that?!

ok next I thought WPS office (Kingsoft) has better compatibility, right. So I install it. and again all animations are loaded, though a bit slow on response it all works in that area. the graph is a no go:
[img]http://shrani.si/f/1G/x2/1rjvBNQJ/wpsoffice1.png[/img]

as a bonus it added some random numbers in one table in the presentation among the text. yeah they seem to be just random numbers at a bit different font some in [SUP]index[/SUP] some  [SUB]down below[/SUB].

I then remembered Caligra office. it has a program Stage. could it do it? Possibly not, but let's see what happens. at first I had a bit of an issue. installing Stage from software centre did nothing. I mean I launched it but nothing appeared on the screen. so I removed it and installed the whole suite. why offer a separate program in the repos if it actually can't work separately form the rest? anyway installing the whole suite made it launch. I open the file and it even asks me what way should it import the file. it imports it but the file is missing all animations, the titles are off (font size, text box placement changed...). how about the graph?
well I got this big question mark starring at me:
[img]http://shrani.si/f/6/Da/r3LuIEc/calligra-stage.png[/img]

is it asking me? I should be asking it "where is my graph?" :)

anyway I just feel a bit let down by the translators. I can understand that there will be issues with macros or some customization but not something as simple as this graph - 2 axis=two table columns one shows dates one quantities. 

how to solve it for simple presentations:
workaround 1 -  use pictures for graphs. the libre office imports it quite well. 
workaround 2 - install MS office 2007 or 2010 in wine. 2007 works quite well in wine. I plan to do this in the future when I have time. for now I will test before hand in libre office and try to use that.

anyone else with a fail story at the last moment?

does anyone know is openoffice is better at importing these things? What about that one that derives from lotus office - I mean they use some modified open office interface (forgot it's name).

also I would really really like to see a standard office format in this world that anyone could work with. I mean compete with great features not with formats! 

just came into my mind I should try to save as ODF in MS office. and then see what happens...

---

