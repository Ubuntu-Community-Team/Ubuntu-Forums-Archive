---
title: "High-precision calculator"
date: 2010-01-16
forum: The Cafe
---

### Post by blazemore on 2010-01-16
Hi can someone please help me?
I need to do some arithmetic with VERY large numbers.
Specifically, I need to work out 16777216!/(786432!*15990784!)
I need to to NOT be rounded off, I need every last digit.
I can't afford mathematica, and I haven't been able to find anything else.
Can someone with Mathematica please save the answer to this in a text file, or can someone point me to an arbitrary-precision calculator that can do factorials?

---

### Post by Rhubarb on 2010-01-16
Uuuugh, 3 large factorial numbers in that equation? ouch.

I'm currently running this with qalculate on a high-spec computer, so I'll report back if and when it completes for you.

---

### Post by blazemore on 2010-01-16
Really, that long?
Wolfram Alpha will do it, but it rounds it off after a couple of hundred digits.

---

### Post by CharlesA on 2010-01-16
Apparently Open Office Spreadsheet doesn't like it at all.

Stupid question but what does the "!" mean?

EDIT: I'm trying it with Qalculate and it's maxing my CPU out. (C2D 3.16Ghz) O_o

---

### Post by freeball1 on 2010-01-16
This might help

[CLICK ME]("http://www79.wolframalpha.com/input/?i=binomial(16777216,786432)")

You have to wait a view seconds for the result and can click 'more digits', but that could be a lot of digits :popcorn:

EDIT Too late, didn't notice the new posts

---

### Post by NoaHall on 2010-01-16
> **CharlesA said:**
> Apparently Open Office Spreadsheet doesn't like it at all.

Stupid question but what does the "!" mean?

Factorial.

---

### Post by blazemore on 2010-01-16
n! = n * (n-1) * (n-2) * ... * 1

eg 5! = 5 * 4 * 3 * 2 * 1 = 120

---

### Post by CharlesA on 2010-01-16
> **NoaHall said:**
> Factorial.

Thanks. Apparently the simple math algorithms in OOo cannot handle factorial(s?) numbers.

> **blazemore said:**
> n! = n * (n-1) * (n-2) * ... * 1

eg 5! = 5 * 4 * 3 * 2 * 1 = 120

Yikes that'll be one hell of a number.

EDIT: I wonder if this could be used as a stress test...

---

### Post by blazemore on 2010-01-16
I have a few of these to do.
I might rent a couple of hours on a high performance Amazon cloud server and get this number-crunching done.

---

### Post by blazemore on 2010-01-16
> **CharlesA said:**
> Thanks. Apparently the simple math algorithms in OOo cannot handle factorial(s?) numbers.



Yikes that'll be one hell of a number.

Exactly.

---

### Post by Frak on 2010-01-16
```
1.0937096640132591332030041886467914419106084821604198833778716463298149334059570571856742567817953794468037918136139760032637148026511739020464514664374275564319647428958721823327947534818887731771214398483909930641573945893891014911467555298150318212166919139583723154841307029092879092592422972549458695557344488973734348818916796005319869548357719773466522205503964097052468635969460793810961167829741369413295758391456600006070430248907927486048159058015512682743348440116478329467731370517781066105582624312241978618761177409013554776383967683910280994040777720217465318041649083175242923733082384533129267023620041466800393113351538089282628872248126943807892960567676393755360841250137132602135968366763556089676870035121238214140558567116667820111137546594553713839642139775811868865593328696026022082532808660492588378697073507664241276027001289735488366155623172404290721182931617465129244089575423101656121856163715755086921215333553367909777168418731444911485334612376494941153222907304559623099195169769301057252278346321517950895248739490054171844688897018439268133222115374638457769364608934236303174941587114614461571228174912508703560486937561878484832264410746814974238471014184312879607820202678707547351393414875138119097580678046149646160336097569927368182400254100931307896241361212610626597974362867989157830736236192798501595832882209508903179882626246062283521370647029698588110855585462649188394221258729205685041884142092235997266554301273976482131915579826274717850816902557084160393217031190789029947762656635885278624148811615152934941272042435720210810753297659796846476344092359384271987942592268847948762154013473103665314067235480281243587092131170062282954394329074065141062306167921435007415016203200512922151054441159870340746619657686161443863199371251730650889056598744811510278647780568470740820213083387074895966680142414961563387899539166977394391378530174564401399022754689255276807316114503351393477467289009213368931470376543084163093961703634786183843180681546029739398319818922132844538650564991124570197385072843018793949508714367391346915863676023129335754716756287222254737118185867928262406764697171908937425002287272155745393028829319555391727407256353588552086433915767731157680048517345920935350848609537082756005739869271212780669843106368488351608140261739748639861070976873504524958046228775718267823243555642091879036418222193683677354165660458148318494797477509349049109861117258530231542475878789014751341384812070544781595237115967303767338073449089399163004472852844414087997734670518923442727516089024146486814121214480899842766434666174361161910765867137209711783151409851840351280815067996904622252456463567080924533819175365578264939836576129274707623139786625096885958217114001065421769352885487320541604052735937682913212326205020605501346439549287287370893690393929558136151855993970559261416792868872318917433575185147475082598960617915353899240149587590882772252916363834222492014522993849161918369034077594215330600872166509987562373034760457862611506967437182366112431937494198401898545590500569347918447800100089303948960050784752696160497616391867262530330312295046348883358717886872745266761586829018942073122630995439278611894542609205973059959098023843774260282650784394749653118449526966344034261571086220398026984654022365217027876534645335688027952981657472322574661970971742160744315835648627557872826609237853281118913873643714694586797046489620174532790202314578595704103611506216069582649255736199849749260612530252631521515688823947579088869763245732513464153077138055742934966516272548611726846777007169862108214725530082214099199576497274773445836418518154129093521939676025796398163207421386023040632534740485373... x 10^1378621
```

That's a lot lot lot lot lot.

---

### Post by CharlesA on 2010-01-16
As a sidenote: When I googled the formula I got this as the first hit.

[http://rybkaforum.net/cgi-bin/rybkaforum/topic_show.pl?tid=12471](http://rybkaforum.net/cgi-bin/rybkaforum/topic_show.pl?tid=12471)

O_O

---

### Post by Rhubarb on 2010-01-16
This could be a good project for [http://projecteuler.net/](http://projecteuler.net/) to do.
But, they tend to prefer problems that can be solved in under a minute on a mid-range PC with the use of very efficient algorithms.

My concern with using an Amazon cloud to do the number crunching, is that you probably will need a multithreaded application to do the work for you.  Even working out 786432! is taking 10+ minutes (and counting) so far.
So your first step would be how to code up a number crunching app to evenly distribute an efficient algorithm across many cores.

By the way, am using a 3.33GHz Core i7 with 6GB DDR3 RAM.

And perhaps more importantly, why do you need the full number for?  My guess is that it'd be a rather large text file :P

Edit1: 786432! ~ 7.5756589E4294996
So it seems qualculate isn't good enough for the job.

Edit2: It seems the setting I had for qalculate was "try exact" rather than exact.  Trying again ...

Edit3: Qalculate can't work an answer (to 786432!), even in "exact" mode - it just spits out ~ 7.5756589E4294996
So if it can't work out 786432!, there's no chance it can work out the full expression.
I'll look for another calculator app that should do the job.

---

### Post by CharlesA on 2010-01-16
> **Rhubarb said:**
> 
By the way, am using a 3.33GHz Core i7 with 6GB DDR3 RAM.

And perhaps more importantly, why do you need the full number for?  My guess is that it'd be a rather large text file :P

You sir, will definitely beat me if my machine can even handle it.

---

### Post by Rhubarb on 2010-01-16
As Qalculate isn't suitable, I'm now using apcalc to calculate it.
```
calc -f full_expression.txt > full_answer.txt
```


Where full_expression.txt is:
> 16777216!/(786432!*15990784!)

I'm also running another core to find the answer of 786432! to see if this is remotely feasible to calculate (if it can calculate this in not too long of a time, the answer can be made available reasonably).

Edit1: Ok, it's found the answer to 786432!  It makes for a 4.1MB text file!!!!!!!! ouch (didn't take to long for it to calculate either)
I'll let it run the full expression, and let you know when I get the answer for it.

---

### Post by Mr. Picklesworth on 2010-01-16
Qalculate and Python (with ipython) both make excellent calculators, and will happily deal with enormous numbers :)

---

### Post by Frak on 2010-01-16
> **Mr. Picklesworth said:**
> Qalculate and Python (with ipython) both make excellent calculators, and will happily deal with enormous numbers :)
I'm fond of Ruby and Bignum.

---

### Post by Rhubarb on 2010-01-17
I'm starting to wonder if I've got the disk space and / or the time to run this calculation.

My poor brain is under the weather at the moment as I've got a cold.  So I'm not sure if this problem can be solved on a computer (or cloud) with today's hardware, and perhaps more importantly, an answering that fits in a practical file size.

It's been 2 hours and I still haven't come up with a result for 15990784!

I'm guessing there should be a way to simplify this to make it a more manageable to process.  I'm not much of a mathematician myself.

---

### Post by Mr. Picklesworth on 2010-01-17
This is odd:
[http://www.google.ca/search?hl=en&source=hp&q=16777216%21%2F%28786432%21*15990784%21%29&btnG=Google+Search&meta=&aq=f&oq=](http://www.google.ca/search?hl=en&source=hp&q=16777216%21%2F%28786432%21*15990784%21%29&btnG=Google+Search&meta=&aq=f&oq=)

---

### Post by Rhubarb on 2010-01-17
I've given up on this I'm sorry to say.
It's simply too big of a number :P

Interesting thread though, I might try to simplify this when my head feels better someday.

---

### Post by lostinxlation on 2010-01-17
16777216!/(786432!*15990784!) 
 
You can simplify it by eliminating 15990784! and run multiplication from 16777216 to 15990785 followed by division by 786432!.
 
 
Difficult part is calculating in the great precision. Even 64bit CPU can express around up to 10^20 ish so that if you need an great precision, the program needs to have some algorithm to deal with the number that exceeds the bit capacity the cpu has.
 
After being simplyfied, it is going to be like (16777216/786432)*(16777215/786431)* .......... *(15990785/1) and you can guess how huge the final number would be. Just being super conservative and replacing evey term with 10, it still goes up to more than 10^786432. That's a crazy number.

---

### Post by whiskeylover on 2010-01-17
10^1million+?

Thats a huge freaking number!

---

### Post by blazemore on 2010-01-17
> **Frak said:**
> ```
1.0937096640132591332030041886467914419106084821604198833778716463298149334059570571856742567817953794468037918136139760032637148026511739020464514664374275564319647428958721823327947534818887731771214398483909930641573945893891014911467555298150318212166919139583723154841307029092879092592422972549458695557344488973734348818916796005319869548357719773466522205503964097052468635969460793810961167829741369413295758391456600006070430248907927486048159058015512682743348440116478329467731370517781066105582624312241978618761177409013554776383967683910280994040777720217465318041649083175242923733082384533129267023620041466800393113351538089282628872248126943807892960567676393755360841250137132602135968366763556089676870035121238214140558567116667820111137546594553713839642139775811868865593328696026022082532808660492588378697073507664241276027001289735488366155623172404290721182931617465129244089575423101656121856163715755086921215333553367909777168418731444911485334612376494941153222907304559623099195169769301057252278346321517950895248739490054171844688897018439268133222115374638457769364608934236303174941587114614461571228174912508703560486937561878484832264410746814974238471014184312879607820202678707547351393414875138119097580678046149646160336097569927368182400254100931307896241361212610626597974362867989157830736236192798501595832882209508903179882626246062283521370647029698588110855585462649188394221258729205685041884142092235997266554301273976482131915579826274717850816902557084160393217031190789029947762656635885278624148811615152934941272042435720210810753297659796846476344092359384271987942592268847948762154013473103665314067235480281243587092131170062282954394329074065141062306167921435007415016203200512922151054441159870340746619657686161443863199371251730650889056598744811510278647780568470740820213083387074895966680142414961563387899539166977394391378530174564401399022754689255276807316114503351393477467289009213368931470376543084163093961703634786183843180681546029739398319818922132844538650564991124570197385072843018793949508714367391346915863676023129335754716756287222254737118185867928262406764697171908937425002287272155745393028829319555391727407256353588552086433915767731157680048517345920935350848609537082756005739869271212780669843106368488351608140261739748639861070976873504524958046228775718267823243555642091879036418222193683677354165660458148318494797477509349049109861117258530231542475878789014751341384812070544781595237115967303767338073449089399163004472852844414087997734670518923442727516089024146486814121214480899842766434666174361161910765867137209711783151409851840351280815067996904622252456463567080924533819175365578264939836576129274707623139786625096885958217114001065421769352885487320541604052735937682913212326205020605501346439549287287370893690393929558136151855993970559261416792868872318917433575185147475082598960617915353899240149587590882772252916363834222492014522993849161918369034077594215330600872166509987562373034760457862611506967437182366112431937494198401898545590500569347918447800100089303948960050784752696160497616391867262530330312295046348883358717886872745266761586829018942073122630995439278611894542609205973059959098023843774260282650784394749653118449526966344034261571086220398026984654022365217027876534645335688027952981657472322574661970971742160744315835648627557872826609237853281118913873643714694586797046489620174532790202314578595704103611506216069582649255736199849749260612530252631521515688823947579088869763245732513464153077138055742934966516272548611726846777007169862108214725530082214099199576497274773445836418518154129093521939676025796398163207421386023040632534740485373... x 10^1378621
```

That's a lot lot lot lot lot.
It's also rounded off.

---

### Post by blazemore on 2010-01-17
> **lostinxlation said:**
> 16777216!/(786432!*15990784!) 
 
You can simplify it by eliminating 15990784! and run multiplication from 16777216 to 15990785 followed by division by 786432!.
 
 
Difficult part is calculating in the great precision. Even 64bit CPU can express around up to 10^20 ish so that if you need an great precision, the program needs to have some algorithm to deal with the number that exceeds the bit capacity the cpu has.
 
After being simplyfied, it is going to be like (16777216/786432)*(16777215/786431)* .......... *(15990785/1) and you can guess how huge the final number would be. Just being super conservative and replacing evey term with 10, it still goes up to more than 10^786432. That's a crazy number.

It's not that crazy, it's 786433 digits long

---

### Post by blazemore on 2010-01-17
> **Rhubarb said:**
> I'm starting to wonder if I've got the disk space and / or the time to run this calculation.

My poor brain is under the weather at the moment as I've got a cold.  So I'm not sure if this problem can be solved on a computer (or cloud) with today's hardware, and perhaps more importantly, an answering that fits in a practical file size.

It's been 2 hours and I still haven't come up with a result for 15990784!

I'm guessing there should be a way to simplify this to make it a more manageable to process.  I'm not much of a mathematician myself.

Is calc included by default?

---

### Post by ratcheer on 2010-01-17
The ***ruby*** programming language can act as a calculator and I have seen it work accurately with numbers hundreds of digits long. It would only take a short tutorial session to learn how to use it, this way.

Tim

---

### Post by blazemore on 2010-01-17
Accuracy is one thing, precision another.
I do not want the answer to be x * 10^n
I need it to be fully expanded with every place value fully represented.

---

### Post by blazemore on 2010-01-17
> **Rhubarb said:**
> 
Edit1: Ok, it's found the answer to 786432!  It makes for a 4.1MB text file!!!!!!!! ouch (didn't take to long for it to calculate either)
I'll let it run the full expression, and let you know when I get the answer for it.

Could you please attach the text file, at least it would make my life a bit easier!

---

### Post by ratcheer on 2010-01-17
> **blazemore said:**
> Accuracy is one thing, precision another.
I do not want the answer to be x * 10^n
I need it to be fully expanded with every place value fully represented.

ruby will do that.

Tim

---

### Post by blazemore on 2010-01-17
I know nothing of ruby syntax.
Could you please tell me the quick ruby script that can do this?
I could probably do it in Python with the Math module, but I heard Python was slow for this kind of calculation.

---

### Post by jwbrase on 2010-01-17
> **blazemore said:**
> It's not that crazy, it's 786433 digits long

Plus anything after the decimal point.

---

### Post by TheLions on 2010-01-17
here you go:
[http://www.wolframalpha.com/input/?i=16777216!%2F%28786432!*15990784!%29](http://www.wolframalpha.com/input/?i=16777216!%2F%28786432!*15990784!%29)

result: 10^(10^6.139444901903225)

---

### Post by Marlonsm on 2010-01-17
It is an integer, without decimals.
It seems to come from the formula "Count = N!/(P!*(N-P)!)" with N = 16777216 and P = 786432.
And all the results generated by it should have no decimals, as it shows the number of possibilities for something to happen.

I've googled that equation and I found this page: [http://rybkaforum.net/cgi-bin/rybkaforum/topic_show.pl?tid=12471](http://rybkaforum.net/cgi-bin/rybkaforum/topic_show.pl?tid=12471)
It comes from this post:
> Your already staring at the thing that's more complex than most of all board games. Your monitor is more complex than any board game if the entire board game can fit on your screen. Let's say red,green,blue color combination 256^3 then 16777216 possible colors that can happen to a single pixel. If you got 1024x768 monitor, let's calculate all the possible images that you can see there. Then you got 786432 number of pixels, using permutations you get 16777216!/(786432!*15990784!) possible combination (my computer can't handle this equation now without using special solving softwares) but of course the colors of that don't repeat yet just the combination supposing of using unique colors in the pixels so you add exponents again of all colors (16777216!/(786432!*15990784!))^16777216. Supposing my approximation is correct no board game should exceed the complexity of that number if it can fit on the screen as that is number of all possible images you can see on your monitor.
If he is right, it shows the number of possible images in a 1024x768 using 24 bit colours not repeating any colour, but as far I know know maths, it actually shows the number of possible combinations of colours you can have in that monitor.

And I disagree with him in the second part, the equation for all possible images repeating colours would be 16777216^786432 (number of colours ^ number of pixels), or 2^18874368, something like 10^62699293, which also means the number we are looking for is (much) smaller than 62699294 digits.

---

### Post by jomiolto on 2010-01-17
Here's the number as a compressed text file. It's only 1,378,622 digits! ;)

Hopefully it's correct; the first digits are the same as Frak calculated, so it should be.

Edit: as Marlonsm said, it divided in to an integer. No decimals.

---

### Post by Marlonsm on 2010-01-17
> **jomiolto said:**
> Here's the number as a compressed text file. It's only 1,378,622 digits! ;)

Hopefully it's correct; the first digits are the same as Frak calculated, so it should be.

Edit: as Marlonsm said, it divided in to an integer. No decimals.

Just a question, where did you calculate it?

---

### Post by jomiolto on 2010-01-17
> **Marlonsm said:**
> Just a question, where did you calculate it?

I wrote a small C program using the [GNU Multiple Precision library]("http://gmplib.org/"). It took only about 10-15 minutes for my slow laptop to calculate :)

---

### Post by blazemore on 2010-01-17
You're quite right. I'm trying to calculate the number of possible images at 1024 x 768.

Perhaps I should have made this clear earlier, in case there was a problem with my maths.
That attachment, is it the absolute, final answer? Or just one of the factorials?

---

### Post by jomiolto on 2010-01-17
> **blazemore said:**
> You're quite right. I'm trying to calculate the number of possible images at 1024 x 768.

Perhaps I should have made this clear earlier, in case there was a problem with my maths.
That attachment, is it the absolute, final answer? Or just one of the factorials?

It is the final answer.

---

### Post by Frak on 2010-01-17
I've been calcuating this thing for the past two hours. Should be done soon.

---

### Post by ratcheer on 2010-01-17
> **blazemore said:**
> I know nothing of ruby syntax.
Could you please tell me the quick ruby script that can do this?
I could probably do it in Python with the Math module, but I heard Python was slow for this kind of calculation.

```

[COLOR=#9966cc]**def**[/COLOR] factorial[COLOR=#006600]**(**[/COLOR]n[COLOR=#006600]**)**[/COLOR]
  [COLOR=#9966cc]**if**[/COLOR] n == [COLOR=#006666]0[/COLOR]
    [COLOR=#006666]1[/COLOR]
  [COLOR=#9966cc]**else**[/COLOR]
    n * factorial[COLOR=#006600]**(**[/COLOR]n[COLOR=#006666]-1[/COLOR][COLOR=#006600]**)**[/COLOR]
  [COLOR=#9966cc]**end**[/COLOR]
[COLOR=#9966cc]**end**[/COLOR]
``````

irb(main):014:0> factorial(200)
=> 788657867364790503552363213932185062295135977687173263294742533244359449963403342920304284011984623904177212138919638830257642790242637105061926624952829931113462857270763317237396988943922445621451664240254033291864131227428294853277524242407573903240321257405579568660226031904170324062351700858796178922222789623703897374720000000000000000000000000000000000000000000000000

```Tim

---

### Post by Frak on 2010-01-17
> **ratcheer said:**
> ```

[COLOR=#9966cc]**def**[/COLOR] factorial[COLOR=#006600]**(**[/COLOR]n[COLOR=#006600]**)**[/COLOR]
  [COLOR=#9966cc]**if**[/COLOR] n == [COLOR=#006666]0[/COLOR]
    [COLOR=#006666]1[/COLOR]
  [COLOR=#9966cc]**else**[/COLOR]
    n * factorial[COLOR=#006600]**(**[/COLOR]n[COLOR=#006666]-1[/COLOR][COLOR=#006600]**)**[/COLOR]
  [COLOR=#9966cc]**end**[/COLOR]
[COLOR=#9966cc]**end**[/COLOR]
``````

irb(main):014:0> factorial(200)
=> 788657867364790503552363213932185062295135977687173263294742533244359449963403342920304284011984623904177212138919638830257642790242637105061926624952829931113462857270763317237396988943922445621451664240254033291864131227428294853277524242407573903240321257405579568660226031904170324062351700858796178922222789623703897374720000000000000000000000000000000000000000000000000

```Tim
If n is too large, it will overflow the stack. I extended the Integer object like so

```
class Integer
  def fact
    return 1 if self == 0
    (1..self).inject { |a,b| a*b }
  end
end
```

Now I can call any number with .fact to convert the number to its factorial representation. 3.fact returns 6.

---

### Post by lisati on 2010-01-17
> **lostinxlation said:**
> 16777216!/(786432!*15990784!) 
 
You can simplify it by eliminating 15990784! and run multiplication from 16777216 to 15990785 followed by division by 786432!.
 
 
Difficult part is calculating in the great precision. Even 64bit CPU can express around up to 10^20 ish so that if you need an great precision, the program needs to have some algorithm to deal with the number that exceeds the bit capacity the cpu has.
 
After being simplyfied, it is going to be like (16777216/786432)*(16777215/786431)* .......... *(15990785/1) and you can guess how huge the final number would be. Just being super conservative and replacing evey term with 10, it still goes up to more than 10^786432. That's a crazy number.
Reading through this thread I had some vague recollection of shortcuts and simplifications such as the above being available to help speed up the process without sacrificing accuracy. It has been a long time, and I need a coffee!

---

### Post by ratcheer on 2010-01-17
Ok. I am something of a newbie at Ruby, myself. Good work.

Tim

---

### Post by cguy on 2010-01-17
Damn, guys! Don't bother calculating THAT! It's horrible!
You can **simplify it a thousand times** before you'd have to do any large number multiplication or division.

Besides that **factorial simplification** mentioned 2 pages ago you can:
**a)** see who is a divisor/multiple of who

**b)** split everything into divisors and base your calculation on them.
eg: 21 / 14 * 3 = bad
21 = 7*3
14 = 7*2
3 = 3
Now we construct 3 vectors:
values: 7 | 3 | 2
powers: 1 | 1 | 0 (with plus)
powers: 1 | 1 | 1 (with minus)
Substract the last vectors (or combine them into 1 before starting!) and you will only divide 1 to 2.
Easier, eh?

**c)** a+b

Noone ever in science will do what you want to do here because it's stupid and requires a huge amount of work. Everybody wants smart solutions.

---

### Post by Frak on 2010-01-17
I've capped my calcuating process to 50%. I'm only running on a dual-core, but if this takes longer, I'll shift the work over to my PowerMac G4 to run in a dedicated session.

---

### Post by bjergtrolden on 2010-01-17
1.0937096640132591332030041886467914419106084821604198833778716463298149334059570571856742567817953794468037918136139760032637148026511739020464514664374275564319647428958721823327947534818887731771214398483909930641573945893891014911467555298150318212166919139583723154841307029092879092592422972549458695557344488973734348818916796005319869548357719773466522205503964097052468635969460793810961167829741369413295758391456600006070430248907927486048159058015512682743348440116478329467731370517781066105582624312241978618761177409013554776383967683910280994040777720217465318041649083175242923733082384533129267023620041466800393113351538089282628872248126943807892960567676393755360841250137132602135968366763556089676870035121238214140558567116667820111137546594553713839642139775811868865593328696026022082532808660492588378697073507664241276027001289735488366155623172404290721182931617465129244089575423101656121856163715755086921215333553367909777168418731444911485334612376494941153222907304559623099195169769301057252278346321517950895248739490054171844688897018439268133222115374638457769364608934236303174941587114614461571228174912508703560486937561878484832264410746814974238471014184312879607820202678707547351393414875138119097580678046149646160336097569927368182400254100931307896241361212610626597974362867989157830736236192798501595832882209508903179882626246062283521370647029698588110855585462649188394221258729205685041884142092235997266554301273976482131915579826274717850816902557084160393217031190789029947762656635885278624148811615152934941272042435720210810753297659796846476344092359384271987942592268847948762154013473103665314067235480281243587092131170062282954394329074065141062306167921435007415016203200512922151054441159870340746619657686161443863199371251730650889056598744811510278647780568470740820213083387074895966680142414961563387899539166977394391378530174564401399022754689255276807316114503351393477467289009213368931470376543084163093961703634786183843180681546029739398319818922132844538650564991124570197385072843018793949508714367391346915863676023129335754716756287222254737118185867928262406764697171908937425002287272155745393028829319555391727407256353588552086433915767731157680048517345920935350848609537082756005739869271212780669843106368488351608140261739748639861070976873504524958046228775718267823243555642091879036418222193683677354165660458148318494797477509349049109861117258530231542475878789014751341384812070544781595237115967303767338073449089399163004472852844414087997734670518923442727516089024146486814121214480899842766434666174361161910765867137209711783151409851840351280815067996904622252456463567080924533819175365578264939836576129274707623139786625096885958217114001065421769352885487320541604052735937682913212326205020605501346439549287287370893690393929558136151855993970559261416792868872318917433575185147475082598960617915353899240149587590882772252916363834222492014522993849161918369034077594215330600872166509987562373034760457862611506967437182366112431937494198401898545590500569347918447800100089303948960050784752696160497616391867262530330312295046348883358717886872745266761586829018942073122630995439278611894542609205973059959098023843774260282650784394749653118449526966344034261571086220398026984654022365217027876534645335688027952981657472322574661970971742160744315835648627557872826609237853281118913873643714694586797046489620174532790202314578595704103611506216069582649255736199849749260612530252631521515688823947579088869763245732513464153077138055742934966516272548611726846777007169862108214725530082214099199576497274773445836418518154129093521939676025796398163207421386023040632534740485373... x 10^1378621

---

### Post by Frak on 2010-01-17
> **bjergtrolden said:**
> 1.0937096640132591332030041886467914419106084821604198833778716463298149334059570571856742567817953794468037918136139760032637148026511739020464514664374275564319647428958721823327947534818887731771214398483909930641573945893891014911467555298150318212166919139583723154841307029092879092592422972549458695557344488973734348818916796005319869548357719773466522205503964097052468635969460793810961167829741369413295758391456600006070430248907927486048159058015512682743348440116478329467731370517781066105582624312241978618761177409013554776383967683910280994040777720217465318041649083175242923733082384533129267023620041466800393113351538089282628872248126943807892960567676393755360841250137132602135968366763556089676870035121238214140558567116667820111137546594553713839642139775811868865593328696026022082532808660492588378697073507664241276027001289735488366155623172404290721182931617465129244089575423101656121856163715755086921215333553367909777168418731444911485334612376494941153222907304559623099195169769301057252278346321517950895248739490054171844688897018439268133222115374638457769364608934236303174941587114614461571228174912508703560486937561878484832264410746814974238471014184312879607820202678707547351393414875138119097580678046149646160336097569927368182400254100931307896241361212610626597974362867989157830736236192798501595832882209508903179882626246062283521370647029698588110855585462649188394221258729205685041884142092235997266554301273976482131915579826274717850816902557084160393217031190789029947762656635885278624148811615152934941272042435720210810753297659796846476344092359384271987942592268847948762154013473103665314067235480281243587092131170062282954394329074065141062306167921435007415016203200512922151054441159870340746619657686161443863199371251730650889056598744811510278647780568470740820213083387074895966680142414961563387899539166977394391378530174564401399022754689255276807316114503351393477467289009213368931470376543084163093961703634786183843180681546029739398319818922132844538650564991124570197385072843018793949508714367391346915863676023129335754716756287222254737118185867928262406764697171908937425002287272155745393028829319555391727407256353588552086433915767731157680048517345920935350848609537082756005739869271212780669843106368488351608140261739748639861070976873504524958046228775718267823243555642091879036418222193683677354165660458148318494797477509349049109861117258530231542475878789014751341384812070544781595237115967303767338073449089399163004472852844414087997734670518923442727516089024146486814121214480899842766434666174361161910765867137209711783151409851840351280815067996904622252456463567080924533819175365578264939836576129274707623139786625096885958217114001065421769352885487320541604052735937682913212326205020605501346439549287287370893690393929558136151855993970559261416792868872318917433575185147475082598960617915353899240149587590882772252916363834222492014522993849161918369034077594215330600872166509987562373034760457862611506967437182366112431937494198401898545590500569347918447800100089303948960050784752696160497616391867262530330312295046348883358717886872745266761586829018942073122630995439278611894542609205973059959098023843774260282650784394749653118449526966344034261571086220398026984654022365217027876534645335688027952981657472322574661970971742160744315835648627557872826609237853281118913873643714694586797046489620174532790202314578595704103611506216069582649255736199849749260612530252631521515688823947579088869763245732513464153077138055742934966516272548611726846777007169862108214725530082214099199576497274773445836418518154129093521939676025796398163207421386023040632534740485373... x 10^1378621
That's rounded.

---

### Post by blazemore on 2010-01-17
Okay I'm going to rent some Amazon EC2 time.

---

### Post by cguy on 2010-01-17
@the guy with the i7:
Save that code in a file named a.py and run python with
python a.py
and post the last 4 lines, please.

On my Athlon single code 1.8GHz, opera with 6 tabs, Transmission, Calculator, a big Image displayed, the System Monitor running and Gedit started takes a while to finish.


I hope the code is correct (didn't check it thoroughly), but it definitely isn't efficient.



edit: Blazemore, did you waste your money on Amazon yet? :)





EDIT: [http://paste.pocoo.org/show/166476/](http://paste.pocoo.org/show/166476/)    <- THIS CODE!!!!!!! :D

---

### Post by blazemore on 2010-01-17
No, but I am going to.
I have a number of these to run. I also need to convert this to base 93. Don't ask.

---

### Post by CharlesA on 2010-01-17
Sounds complicated. :lolflag:

---

### Post by blazemore on 2010-01-17
Yes.
I want to express that number in the smallest possible file.
Base 94 (93 was a typo) uses the ascii characters from ! through to ~
I could use a base higher than 128, but this would require a higher character set, and I don't think the trade-off would be worth it.

---

### Post by cguy on 2010-01-17
1 hour later and my code processed only 300,000 numbers.
Damn, it's slow!


What is the point of this? :)

---

### Post by kelvin spratt on 2010-01-17
[http://freeonlinecalculator.net/index.php](http://freeonlinecalculator.net/index.php)

---

### Post by blazemore on 2010-01-17
I'm really sorry but I don't want to disclose exactly why I'm doing this. I'm doing some preliminary research for a third-year project (I'm currently in my first year of a Computer Science degree), and at the moment I can't get time on the University monster (3.14 terraflops - pathetic in the grand scheme of things, but still the second fastest academic machine in the UK).

---

### Post by blazemore on 2010-01-17
> **kelvin spratt said:**
> [http://freeonlinecalculator.net/index.php](http://freeonlinecalculator.net/index.php)

Did you read the whole thread?

---

### Post by Marlonsm on 2010-01-17
If you want to calculate another one, you can use some math to simplify it.
For example, the 16777216!/(786432!*15990784!) could become: (16777216*16777215*16777214*...*15990786*15990785)/786432!
So the numbers you have to deal with are smaller (it is, "less huge").

Remembering factorials:
N! = N*(N-1)*(N-2)*...*2*1
and
N!/P! (if N>P) = N*(N-1)*...*(P+2)*(P+1)

---

### Post by Dr. C on 2010-01-17
Have you considered Sage? It is a FLOSS alternative to Mathematica and it is available in the repositories.

---

### Post by Fornax-101 on 2010-01-18
> **jomiolto said:**
> Here's the number as a compressed text file. It's only 1,378,622 digits! ;)

Hopefully it's correct; the first digits are the same as Frak calculated, so it should be.

Edit: as Marlonsm said, it divided in to an integer. No decimals.


I got the same answer, so I think it is correct.

You can test it with the code in the attachement:

Compile it: gcc -o run code.c -lgmp -lm
and run it: ./run

---

### Post by ratcheer on 2010-01-18
> **FineE said:**
> Have you considered Sage? It is a FLOSS alternative to Mathematica and it is available in the repositories.

Thanks for that tip. I have downloaded and installed sage and I'm just starting to get my feet wet. It is fascinating.

Tim

---

### Post by red_Marvin on 2010-01-18
> **blazemore said:**
> You're quite right. I'm trying to calculate the number of possible images at 1024 x 768.
Could you elaborate on this? I'm interpreting it as calculating the number possible pixel coloring combinations with no other constraints, which would render a formula of the type 2*(bpp*w*h) which does not look like your formula -hence the question. (eg, for a 1024x768 monochrome image there are [[236740 digits]] of possible combinations)

---

### Post by HermanAB on 2010-01-18
Howdy,

You can probably use SciLab or Octave.  They are free and probably in the repos.

[http://www.scilab.org/](http://www.scilab.org/)
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

---

### Post by insane_alien on 2010-01-18
> **red_Marvin said:**
> Could you elaborate on this? I'm interpreting it as calculating the number possible pixel coloring combinations with no other constraints, which would render a formula of the type bpp**(w*h) which does not look like your formula -hence the question. (eg, for a 1024x768 monochrome image there are [[236740 digits]] of possible combinations)

that gets you the number of bits per pixel, but not the number of images you can represent with it.

---

### Post by red_Marvin on 2010-01-18
Ah, I missed that one, it's 2**(bpp*w*h)

---

### Post by lostinxlation on 2010-01-19
> **blazemore said:**
> You're quite right. I'm trying to calculate the number of possible images at 1024 x 768.
 
Perhaps I should have made this clear earlier, in case there was a problem with my maths.
That attachment, is it the absolute, final answer? Or just one of the factorials?
 
So I'm curious how you derive that equation to find out the possible image count on 1024x768 ?
And since you are looking for the possible image count, the result must be an integer number. but I wonder if the equation really can get an integer number and I highly doubt it by just looking at the equation. It seems contradictory and that makes me think the equation may not be correct.
 
As someone already pointed out, the number of possible image should be 
(number of color per pixel)^(1024*768 ) if the same colors are allowed multiple times.
It's a simple permutation problem, isn't it ?
 
 
PS.
A simplified case study - 4 pixels display and monochrome(0/1).
You can have 0000, 0001, 0010, 0011, 0100, .... 1111. 16 possible images, which also can be derived by 2^4.
If we follow the same equation you have, it goes like 2!/(4!*(-2)!).   Doesn't make sense, does it ?

---

### Post by wannabegeek on 2010-01-19
I don't think Octave will handle it or matlab...they use memory real quick...


my guess  would be to use FORTRAN 90
FORTRAN is what all the bad *** non-linear dynamics people use who I'm trying to get to know....they work with the data on matlab, but crunch with FORTRAN

I 've been told that Python will make function calls to FORTRAN and is good for math 
in general.

good luck!

wbg

---

### Post by BackwardsDown on 2010-01-19
> **lostinxlation said:**
> As someone already pointed out, the number of possible image should be 
(number of color per pixel)^(1024*768 ) if the same colors are allowed multiple times.
It's a simple permutation problem, isn't it ?
 
 
PS.
A simplified case study - 4 pixels display and monochrome(0/1).
You can have 0000, 0001, 0010, 0011, 0100, .... 1111. 16 possible images, which also can be derived by 2^4.
If we follow the same equation you have, it goes like 2!/(4!*(-2)!).   Doesn't make sense, does it ?

I was thinking about the same thing, why does he use factorials? Maybe he wants all the images but not use the same color twice or something?

---

### Post by TyrantWave on 2010-01-19
> **blazemore said:**
> I'm really sorry but I don't want to disclose exactly why I'm doing this. I'm doing some preliminary research for a third-year project (I'm currently in my first year of a Computer Science degree), and at the moment I can't get time on the University monster (3.14 terraflops - pathetic in the grand scheme of things, but still the second fastest academic machine in the UK).

Just out of curiosity, what uni do you go to?

---

### Post by lostinxlation on 2010-01-19
> **BackwardsDown said:**
> I was thinking about the same thing, why does he use factorials? Maybe he wants all the images but not use the same color twice or something?
Yeah, I don't get that either.
 
If I remember my high school math correctly,  the equation he showed, N!/(R!*(N-R)!) is to find out the number of combination when picking R out of N items w/o picking the same items. So, applying this on the display pixels is most certainly meaningless because no geometric information is involved. It's just a collection of possible color combinations.
 
If he wanted to calculate the number of possible images w/o using the same colors twice or more, it must have been N*(N-1)*(N-2)*.......(N-R+1)=N!/(N-R)!, so....I guess  his equation is still incorrect.

---

### Post by blazemore on 2010-01-19
Okay people seem better than me at Maths.

Can someone please help me and give me a formula for:

The number of POSSIBLE IMAGES

of width x
of height y
with 2^n possible colours per pixel (ie n bits per pixel)

---

### Post by Marlonsm on 2010-01-19
> **blazemore said:**
> Okay people seem better than me at Maths.

Can someone please help me and give me a formula for:

The number of POSSIBLE IMAGES

of width x
of height y
with 2^n possible colours per pixel (ie n bits per pixel)

For the first pixel you'll have 2^n possibilities, times 2^n for the second, times 2^n for the third and so on, so it's:
(2^n)^[number of pixels] or (2^n)^(w*h).
Knowing that (x^a)^b = x^(a*b):
The formula you're looking for is 2^(n*w*h)

---

### Post by ssam on 2010-01-19
(2^n)^(x*y)

---

### Post by lostinxlation on 2010-01-19
> **blazemore said:**
> 
The number of POSSIBLE IMAGES
 
of width x
of height y
with 2^n possible colours per pixel (ie n bits per pixel)
Each pixel has 2^n possibility, and you have x*y pixels in total.. The number of possible images would be (2^n)^(x*y).
 
You can always think in the small scale to verify it easily. for example, you have 3 colors per pixel and 2 pixel display.

---

### Post by blazemore on 2010-01-19
Wolfram Alpha makes that 
8.8064374944814641465203942443788439753751043538628... x 10^3787833

Is there an easy way to see how many digits long this would be in a different base?

---

### Post by aaaantoine on 2010-01-19
> **blazemore said:**
> Yes.
I want to express that number in the smallest possible file.
Base 94 (93 was a typo) uses the ascii characters from ! through to ~
I could use a base higher than 128, but this would require a higher character set, and I don't think the trade-off would be worth it.

Your options are...

1. Write up a program that saves the number as binary instead of text (and can also recall the number for later presentation).
2. Compress the text output.
3. Both?  You *might* be able to get an even smaller file if you compress the binary...

---

### Post by blazemore on 2010-01-19
Is there boolean character encoding? How do I encode it as a binary, I know nothing of this. Maybe I will ask my Information Theory professer, he is some leading Documents Engineering person.

---

### Post by lostinxlation on 2010-01-19
> **blazemore said:**
> Wolfram Alpha makes that 
8.8064374944814641465203942443788439753751043538628... x 10^3787833
 
Is there an easy way to see how many digits long this would be in a different base?
 
Off the top of my head, N=base, x=highest order in a given base, Y=your number,
 
N^x < Y < N^(x+1)
 
taking logarithm with a given base,
x < logY < x+1
 
x+1 is the number of digits that Y has.

---

### Post by Marlonsm on 2010-01-19
> **blazemore said:**
> Wolfram Alpha makes that 
8.8064374944814641465203942443788439753751043538628... x 10^3787833

Is there an easy way to see how many digits long this would be in a different base?

The 10^whatever part means that the number is multiplied by 1 followed by "whatever" zeroes.

So that number has 3787833 + 1 = 3787834 digits.

A way to know the amount of digits is finding the logarithm of that number in the base 10, adding 1 and rounding down.

For example log173 = ~2.238, adding 1 = 3.238, rounding down = 3 digits.

The number we are looking for is 2^(b*w*h). It's log in the base 2 would be b*w*h, using the base change property, log(base x)a/log(base y)x = log(base y)a.
So the number of digits is (b*w*h/log2 + 1) rounded down, log 3 is around 0.30103.

But, again, you'll need a high precision calculator to find the actual number, I'll try to do one with the little bit I know of Python.

EDIT: I tried this online Javascript calculator, but after some 20 minutes (and many "program-frozen" alerts) there was no result: [http://www.petting-zoo.org/Calculator.html](http://www.petting-zoo.org/Calculator.html) maybe someone else could try, as in the Help section it's said to be able to find results like 9^(9^9).

I also tried in ActionScript (Adobe Flash's language), it's not the best for it, but it's the one I know. Using this code:
```
onClipEvent(load){
	_root.expo=1;
	_root.result=2;
}
onClipEvent(enterFrame){
	if(_root.expo<12582912){
		_root.expo = _root.expo+1;
		_root.result = _root.result*2;
	}
}
```
It started rounding after some time and then, assuming the result is "Infinity" after about 2^1000.

---

### Post by red_Marvin on 2010-01-19
```
leo@troposphere:~/programmering/avr/t2313test
$ ghci
[...]
Prelude> length $ show $ 2^(1*1024*768)
236740

```
That is the number of digits in base ten for the number of possible images when having one bit per pixel.

---

### Post by Marlonsm on 2010-01-19
I've done a simple python for it, but I couldn't figure out how to output the result to a file:
```

result=4096                 #I could have started at 2, but like this it should be faster
expo=12                     #This is the number "2" is elevated by, so 2^expo = result, our goal is to make expo = 12582912
while expo<12582912:
    result=result*1024      #I've used 1024 instead of 2 because it should get the job done faster
    expo=expo+10            #For every time the result is multiplied by 1024, the exponent gets 10 units bigger
    print expo              #Note this line is just to know how far the result is, remove or comment it for a better performance
while expo==12582912:
                            #Do something to output result to a file
                            #I tried "print result" but got frozen
    expo=expo+1
```

I got to the result after some 20 mins of calcs in my 1st-gen Core 2 Duo but couldn't get the output, trying to print it to the terminal froze it.
All we need to do now is to finish that code and run it.

---

### Post by blazemore on 2010-01-20
```
python code.py > output.txt
```

---

### Post by blazemore on 2010-01-20
Also, I think encoding it in a higher base under an 8-bit character set would be better.
This is because the filesize would be more than 8 times smaller, and it's easier to compress.

---

### Post by humphreybc on 2010-01-20
Mate, I'm second year Software Engineering/Computer Science and the hardest thing I've had to do so far is just a couple of complicated Java programs!

I suggest you try [WETA studios 35,000 core server farm.]("http://blog.dustinkirkland.com/2010/01/39000-core-ubuntu-cluster-renders.html")

---

### Post by blazemore on 2010-01-20
> **humphreybc said:**
> Mate, I'm second year Software Engineering/Computer Science and the hardest thing I've had to do so far is just a couple of complicated Java programs!

I suggest you try [WETA studios 35,000 core server farm.]("http://blog.dustinkirkland.com/2010/01/39000-core-ubuntu-cluster-renders.html")

I don't think they'd let me run my preliminary academic tests. I can use my school's cluster in 2 years' time.

---

### Post by Marlonsm on 2010-01-20
I've run it for almost one hour with no results, it seems to get to the result, but then freezes in the "print result" part.
I've tried smaller numbers and it did work, but not with such a high number.

I've managed to get the number of possible images in a monochrome 1024x768 monitor with this code:
```
result=4096                 #I could have started at 2, but like this it should be faster
expo=12                     #This is the number "2" is elevated by, so 2^expo = result
while expo<786432:
    result=result*1024      #I've used 1024 instead of 2 because it should get the job done faster
    expo=expo+10            #For every time the result is multiplied by 1024, the exponent gets 10 units bigger
print "The number of possible images in a monochrome 1024x768 monitor is:"
print result

```
The output is attached, I had to zip it because the txt file exceeded the forum's size limit.

---

### Post by blazemore on 2010-01-22
I've edited this to work for ANY sized image.
Does this work, or should the expo increment by 2?
```

result = 2
expo = input("Number of bits per pixel: ")
height = input("Height: ")
width = input("Width: ")
pixels = width * height

while expo < pixels:
    result = result * 2
    expo = expo + 1
print "The number of possible images is ",
print result

```

---

### Post by Marlonsm on 2010-01-22
> **blazemore said:**
> I've edited this to work for ANY sized image.
Does this work, or should the expo increment by 2?
```

result = 2
expo = input("Number of bits per pixel: ")
height = input("Height: ")
width = input("Width: ")
pixels = width * height

while expo < pixels:
    result = result * 2
    expo = expo + 1
print "The number of possible images is ",
print result

```

It should increment by 1.
I've just used 1024 and 10 because it runs faster.
BTW, the colour depth is missing in the code, just multiply it by the pixel number.

---

### Post by Ylon on 2010-01-22
> **blazemore said:**
> Hi can someone please help me?
I need to do some arithmetic with VERY large numbers.
Specifically, I need to work out 16777216!/(786432!*15990784!)
I need to to NOT be rounded off, I need every last digit.
I can't afford mathematica, and I haven't been able to find anything else.
Can someone with Mathematica please save the answer to this in a text file, or can someone point me to an arbitrary-precision calculator that can do factorials?

[http://www.google.com/search?q=86432%2A15990784](http://www.google.com/search?q=86432%2A15990784)

---

### Post by Marlonsm on 2010-01-22
> **Ylon said:**
> [http://www.google.com/search?q=86432%2A15990784](http://www.google.com/search?q=86432%2A15990784)

Now try it using the factorials.

And if you read a bit further in the thread, you'll see that what we want now is the result for 2^12582912.

---

### Post by Chronon on 2010-01-22
Mathematica can do 2^12582912.  The raw number is about 3787834 bytes (decimal expansion) so it might take a while to transmit over ssh.

[2^12582912](http://www.uoregon.edu/~jhanniga/largeNum.txt)

---

