---
title: "Chart Software"
date: 2007-06-27
forum: The Cafe
---

### Post by rapha on 2007-06-27
Hi all,

we got to work on a 30-page project work for school and would like to include some bad-*** good-looking diagrams, made with Free Software of course ;) ... I do remember to have seen some such software on freshmeat.net a couple of months ago but can't find it now through either freshmeat.net or Google. Does anybody here know its name maybe?

(I do know about the chart functions of OpenOffice but we were looking for something a bit more slick and individual than out of an office suite)

TIA and best regards from Germany,
Raphael

---

### Post by jiminycricket on 2007-06-27
Could it be "Dia"?

---

### Post by rapha on 2007-06-27
> **jiminycricket said:**
> Could it be "Dia"?

Not quite... Dia is for diagrams in general; it doesn't know how to take a bunch of tabular data and represent it graphically...

---

### Post by daynah on 2007-06-27
I'm interested too. OOo Draw did the job for my last project but I'd love something prettier for the next one.

---

### Post by Dragonbite on 2007-06-27
[[COLOR="Blue"]Pentaho Reporting[/COLOR]]("http://www.pentaho.com/products/reporting/")?

---

### Post by Tundro Walker on 2007-06-27
> **daynah said:**
> I'm interested too. OOo Draw did the job for my last project but I'd love something prettier for the next one.

When working for a previous employer, the director I was working for asked me to do a chart for him...conversation went something like this...

D = Director
M = Me

D: "Hey, I need a chart, and I hear you're a real whiz with Excel."

M: (firing up MS Excel) "Sure.  Just show me where the data is."

D: (confused) "Data?"

M: (also confused) "Um, yeah.  I'm going to need some data to plot the chart in Excel."

D: "Oh, I don't have any data, but I have a good idea what the chart should look like."

M: "..."

D: "Can you just draw me a line that kinda goes like this?" (waves hand in air)

M: (closing down MS Excel...Opening PhotoShop...)

~~~~~~~~~~~~~
I ended up leaving that job shortly after (hard to look at myself in the mirror.  Which, of course, led me to another job, which had almost similar results...

B = Boss
M = Me

M: (pretty concerned) "I got the numbers ran and the pie-charts made.  Doesn't look like our project handling time is that great...at least, not accordingly to company expectations."

B: (concerned, but not so much...) "Hmm..yeah, these numbers look pretty bad.  Say, we've got clients coming in next week.  Alter the numbers to look good, but not **too** good, and post those up so they'll see them.  Then, when they leave, we'll post up the real reports."

M: (not so concerned anymore) "..."

~~~~~~~~~~~~~~~~

So, you see, the moral of the story is...any drawing program makes a wonderful chart tool.  However, any chart made using a drawing program usually doesn't stand up to scrutiny when folks want to see the supporting data.

---

### Post by thisllub on 2007-06-27
Hmmm.

You want to come and help me work on some accounting software.

---

### Post by euler_fan on 2007-06-27
If you don't mind putting in a little elbow grease, I would suggest gnuplot. I use gnuplot's capabilities though R and find it produces very nice looking plots (and that's just with all the defaults) but with some time and effort some amazing things are possible. For tables I would say use LaTeX, export it as a Postscript and embed it into whatever you are doing with it.

Good luck.

---

### Post by rapha on 2007-06-28
Hmmm. Pentaho isn't quite it.

I took a look at some GNUPlot and R tutorials but it does seem to be rather complicated to get started with.
Would you have an example of how to make, say, a pie chart with, say, this for the data:

Oranges: 15%
Apples: 70%
Bananas: 10%
Kiwis: 5%

?

That would be real cool :-)

---

### Post by Dragonbite on 2007-06-28
> **Tundro Walker said:**
> I ended up leaving that job shortly after (hard to look at myself in the mirror.  Which, of course, led me to another job, which had almost similar results...

B = Boss
M = Me

M: (pretty concerned) "I got the numbers ran and the pie-charts made.  Doesn't look like our project handling time is that great...at least, not accordingly to company expectations."

B: (concerned, but not so much...) "Hmm..yeah, these numbers look pretty bad.  Say, we've got clients coming in next week.  Alter the numbers to look good, but not **too** good, and post those up so they'll see them.  Then, when they leave, we'll post up the real reports."

M: (not so concerned anymore) "..."
Makes me think of a joke...

> Guy is interviewing fomr a company Acocuntant. 
First person goes in, a recent graduate from a prestigeous school
The interviewers says "I'm going to ask you only one question."
"What is 2 + 2?"
The graduate, all happy, says "4!"
The interviewer says to the applicant "Thanks for coming by, don't call us, we'll call you."
The next applicant comes in after graduating from a local state college.
The interviewers says "I'm going to ask you only one question."
"What is 2 + 2?"
The applicant thinks for a moment, then says "4."
The interviewer says to the applicant "Thanks for coming by, don't call us, we'll call you."
The third applicant comes in with years of experience at a  Dewy-Cheatum-N-How firm.
The interviewers says "I'm going to ask you only one question."
"What is 2 + 2?"
The applicant pauses for a moment, and looks around.  He gets up and closes the office door.
Leaning over the desk, the applicant asks the interviewer "What do you *want* it to be?"

More recently, though, I was working with somebody here at my company on charts (using Crystal Reports). Anyway, they were asking me (who was there for the technical side only) which way I think the chart should go.  I kept having to go back to "What do you want the chart to say" or "What are *you* trying to show?"

---

### Post by euler_fan on 2007-06-28
> **rapha said:**
> Hmmm. Pentaho isn't quite it.

I took a look at some GNUPlot and R tutorials but it does seem to be rather complicated to get started with.
Would you have an example of how to make, say, a pie chart with, say, this for the data:

Oranges: 15%
Apples: 70%
Bananas: 10%
Kiwis: 5%

?

That would be real cool :-)

Like most things, it's a matter of knowing where to look. I googled "R plot chart" and this was the first link: [How to make a pie chart in R]("http://www.exposurescience.org/heR.doc/library/heR.Activities/html/apie.html").

The options only get more intense from there. If you don't need the statistics and mathematics capabilities of R (or the programming ones for that matter) and/or need a very powerful plotting tool, I still suggest gnuplot.

---

### Post by Tundro Walker on 2007-06-29
> **Dragonbite said:**
> I kept having to go back to "What do you want the chart to say" or "What are *you* trying to show?"

LOL!

In one of Deming's books, he talks about showing a guy a control chart (with upper and lower control limits formulated off averages, etc), and the guy, not know much about statistics said "well, let's just tighten the control lines, that way more things are outside the control limits and we can fix more things at once!"  (something like that)  To which Deming had to reply that the process dictated where the control limits would calculate to.  In order to tighten them, you had to get better control of the process.

I used to laugh about that quip, until I started using control charts at that one job where my boss wanted me to doctor the numbers.  I was using them to show how the overall process had improved since I started working there (through my involvement).  I got so tired of having to explain how I came up with the control limits, what they meant, and what they told us, it was a beating.  I decided to stop using control charts one day when my boss basically said...

"Look, can you get rid of all those extra useless lines on this thing?  I can't read it!"

That pretty much sums it up.  

Now, granted, so you can understand where this company's mentality was, and where my frustration came from...   

M = Me
B = Boss

B: "This chart isn't good at all.  Only 10% of our folks are meeting company standards."

M: "Standards?  I thought that was a goal?"

B: "No...no, that line I had you put there is our company standard."

M: "No...that's a goal.  The standard is actually way down here."

B: (looking at me like I'm retarded) "What?"

M: "A standard is an average work performance that is consistently met by all workers.  A goal is something you're shooting for.  That line there (pointing to the one where only 10% of employees made it past) is a goal...that only 10% of your employees are meeting.  The standard is this line down here."

B: "Huh...I was wondering why you had that line there when I didn't ask you to put it in...."

M: *sigh*

As you can tell, my "egg-headed'ness" didn't gain me much respect at that job, and the sentiment was mutual.  Oh well, that's what happens when a company promotes folks just because they've been there a long time, and not because they actually have skill or education.  As the saying goes, "people are promoted to their level of incompetence."

---

### Post by Dragonbite on 2007-06-29
Found 2 plotting/charting programs while looking through the [[COLOR="Blue"]Mono [/COLOR]]("http://www.mono-project.com/Libraries")website;
[LIST]
[*]NPlot ([[COLOR="Blue"]http://netcontrols.org/nplot/wiki[/COLOR]]("http://netcontrols.org/nplot/wiki")) is a free charting library for .NET and supports various kinds of graphic modes.
[*]ZedGraph ([[COLOR="blue"]http://zedgraph.org[/COLOR]]([COLOR="blue"]http://zedgraph.org[/COLOR])) is a set of classes, written in C#, for creating 2D line and bar graphs of arbitrary datasets. The classes provide a high degree of flexibility -- almost every aspect of the graph can be user-modified. At the same time, usage of the classes is kept simple by providing default values for all of the graph attributes. The classes include code for choosing appropriate scale ranges and step sizes based on the range of data values being plotted.
[/LIST]

---

### Post by rapha on 2007-06-29
Hmmm. That ZedGraph thing is looking quite nice. Although it's even more work than R. Originally I had been looking for some point-and-click tool, but oh well :-)

Btw, what the hell are control charts? Can't get that joke for the hell of it...

---

### Post by euler_fan on 2007-06-29
> **rapha said:**
> Hmmm. That ZedGraph thing is looking quite nice. Although it's even more work than R. Originally I had been looking for some point-and-click tool, but oh well :-)

Btw, what the hell are control charts? Can't get that joke for the hell of it...

So long as you find a tool you like, there's no such thing as too hard.

There's not a joke behind control charts. They're an engineering thing. It actually describes a family of charts used to monitor things like specs in a manufacturing process or some other device that is running. For instance, you might make a temperature over time chart of the steam pressure in a turbine generator at a power plant. What makes this different from a usual line or scatter plot is that it will be centered at the correct operating temperature and have upper and lower limits drawn in so that you know when the temp is getting too high or too low. There may even be multiple ones designating upper and lower ends of the normal operating range, then the mildly out of spec and severely out of spec lines.

---

### Post by Tundro Walker on 2007-06-29
I'll add to what Euler_Fan said...

A [control chart]("http://www.statsoft.com/textbook/stquacon.html") is basically a run chart (you know, typical plotted line chart), except you do 2 additional things to it..

1) you use the runs to calculate the overall average (called x-bar in statistics, since it's denoted by an x with a bar over it...go fig), then plot that on the chart so you can see the run line go up and down across the average line

2) you use the average to plot upper and lower control limits, basically getting the square root of the average, then taking it as a positive or negative and multiply it by 3 to get the upper and lower limits (respectively).  You draw in the UCL & LCL so you can see if any plot points of your run fall in or out of the limits.

The concept is that the square root of the average gives you a standard deviation (a sigma) of the overall process.  By multiplying by 3, you set the control limits to +/- 3 standard deviations (3 sigma) from the average, setting a boundary to which you accept things are either in or out of control.  In Edward Deming's teachings, things that fall within control limits occurred due to normal causes..IE: causes that are part of the process.  plot points falling outside control limits are deemed "special causes", meaning that something outside of the normal process caused those things to occur.

The idea is that, after monitoring a process for a while, and plotting it on a chart, you can do the control limits to see...

1) if anything special is driving things out of control (control limits).  If things are falling outside control limits, then you need to figure out what's causing that and fix it.

2) you can also see how much control you have over the process.  If you have a huge distance between upper and lower control limits, you have loose control over the process, because you're plot points (which ultimately calculated the control limits) are all over the place.  Usually, you can see trends in the plot points, like saw-toothing (IE: sporadic high's followed by sudden low's) or runs, like a lot of points going high, then going low for several plot points.  You can analyze these to see if something is affecting your process, and once you find out what it is, you can control it better.

3) You can use the control chart to monitor progress in gaining more control over the process.  As you fix things that are wrong, you should notice plot points no longer fall out side control limits.  However, you don't just stop there.  You can tweak the process and watch the control limits narrow, and even the whole control limit line drop down notches if you're using it to monitor defects or such.

I'll use an example from my current job (where I'm allowed the eccentricity of control charts, but folks I work with still don't quite understand their use).  I use control charts to monitor sales reps that hand out sales promotions.  We don't want them abusing the promotion if at all possible, because it means we're losing money on the sale.  (EG: if the sales rep could have sold the customer without offering them $5 off for a couple months service, then we'd ideally like to get the customer without the promo.  But, if need be, the rep can use the promo as a final enticement to sell a customer who looks like they're going to bail.)

In monitoring the charts, I notice days when the plots go out of control limits.  I walk up to the sales managers, ask them if anything out of the ordinary happened on such and such day (the day the plot went out of control), and sure enough they say "yeah, as a matter of fact..."  After I get them to admit what went wrong, I can figure out if there was a problem with the process, or perhaps a problem with training.  What I usually find is that there was a new group of sales reps that came in, and the sale team (being a sales team) didn't train them properly, so the new sales reps were abusing the promotion give aways like crazy.  So, I scold the sales managers..again... (for skimping on the training), scold the training department...again... (for not forcing more training on the sales reps), etc, etc.  In the end, being an American business, my findings are usually ignored, and everybody goes on screwing things up...business as usual.  And, eventually, I get tired of harping on them, and just let them dig their own grave.

That's for an external dept that I monitor (baby-sit) though (which, I can understand why they try to ignore me...I'm seen as a matrix manager...I'm not their boss, so they don't want to listen to me, even if it means their job suffers for it).  

For internal use, I use the control charts to monitor work I have direct control over, and my boss and I use it as a dashboard metric for executives so they know they can ignore us because we're doing our jobs properly.

Oh yeah, the in-joke about the guy Deming was talking to about "just draw the control limits closer"...  Since the control limits are calculated based on how the process is doing, you can't just "draw them closer".  To do so would basically be saying "I'll ignore what the chart says my process is actually doing, and instead just draw some lines that I think look nice to make the process look like it's doing what I want."

EDIT: As the MythBusters say ... "I reject your reality, and substitute my own!"

---

