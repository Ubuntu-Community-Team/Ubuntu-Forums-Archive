---
title: "help developing a new program please"
date: 2015-09-12
forum: Ubuntu Application Development
---

### Post by isaiah4 on 2015-09-12
Can Ubuntu be used to create semi-complex input-output programs?                                                                                                                  
I would like to design a program that can either be viewed on a website or downloaded to a computer. The program would ask the user to input some information like their height, weight, age, BMI, and some other relevant questions, and then there would be results including which vitamins and minerals they need, how many, how frequently, which foods include the nutrients and how many are included per serving. then i would like them to be able to select ingredients from the list of foods supplied and then display a list of recipes they can make with the selected ingredients, as well as a display of the nutrient totals given from the ingredients.

If anybody is interested, I would appreciate help developing the program, as I haven't made any programs before. However, any advice or references to free software to help with developing such a program would be appreciated.

Thanks!

---

### Post by TheFu on 2015-09-13
Yes. Any computer can do that.

Most people new to programming should start by learning python. There are many free books, many youtube training videos, many local Py-groups, MIT has Python videos+materials+assignments online for free  - but you need to sit down and do the work.  Oh - and google had some free python training online too - check EdEx as well.

BTW, what you've described doesn't seem very complicated.

---

### Post by isaiah4 on 2015-09-13
Thanks!
Can you tell me what I'd need to learn about Python to be able to make it?
I'm not very interested in designing any software other than the program I mentioned, so learning only what I need to know would help.
Thanks again.

---

### Post by QIII on 2015-09-13
Hello!

What you need to learn is a significant part of the language.  It's impossible to know up front the 7 out of thousands of things you might need to know for an application like that, as simple as it may be in concept.  As indicated, the does not seem at all complicated ... to guys like me who have been wasting our youth on computers since the 70s.  

I speak German.  If you wanted to do something in Germany, I could give you 7 sentences I thought might be the most useful to do what you wanted to do there.  But if you went there and you did not speak the language, it would be hard to get by if you were only given 7 sentences someone thought you might need.  (Disregard the fact that there are so many people there who speak English that it wouldn't be a problem for you to find English speakers. :) )

---

### Post by brian-mccumber on 2015-09-13
I think he was just suggesting that you learn how to program using python. Once you learn basic programming structures and procedures you can use pretty much any language that you want to use. The web based part of your application wouldn't have the problem of platform compatibility because browser based apps will run on pretty much any platform including mobile, but when you venture into the zone of downloadable applications you must take into consideration which systems you want to target and if you want to target them all then you must pick a language that will compile and run on multiple operating systems and you have to take into account that not all peoples systems will be set up to run a specific language, like python for example. Python comes installed on Ubuntu from the get go but Windows users and possibly Mac users must install python on their machine before they could run your app and most normal users won't want to do that just to run your app. And even then you will have to have different distribution methods for different operating systems and I am not even touching on mobile platforms. I mean it's nice to just jump into things sometimes and I like your enthusiasm but in reality there is alot you will probably have to learn first in order to start creating your application.

---

### Post by isaiah4 on 2015-09-13
thanks, but i want to make sure i know the 7 sentences i know i need to know along with the rest of the common words :D

---

### Post by lisati on 2015-09-14
I'd recommend making sure you have a clear idea of what you want your app to do first. Things to consider include where it's getting its data from, what processing you want your app to do on the data, and what form the output should have.  

It might also be a good idea to focus on developing your app for one environment at a time - if you do this step well, porting to another environment will be easier.

---

### Post by isaiah4 on 2015-09-14
thanks lisati
i plan on compiling all of the possibly needed information into some sort of data base for the program to get the data from.  i want the app to process the user input information and output the required nutrient amounts and how often they need them.  
the output doesn't have to look fancy, simply a list of all they need would be fine.  
i plan on it being available on a website so anybody can access it if they have internet.  
the complicated thing i can imagine is how to factor all of the variables together to match the nutrient needs... 
for example, maybe a 150 lb person needs certain things, but at every age they'll need different amounts of them, and may need more or less things also.  how to factor all variables into the output may be tricky and i'll have to do some research unless somebody can tell me how to do it.

---

### Post by Bucky Ball on 2015-09-14
If you don't know how to code this, that is going to be the trickiest part. We can give advice but you're going to need to do the work. Very doubtful anyone here is going to code up the whole thing for you, but they can help you do it yourself.

Are you a nutritionist or you are just interested in how you would get this program together? Are you au fait with programming? Are you developing this as a hobbyist, student, or professional?

My advice would be to start at the beginning: gather your data together, work out how to get it into a database and what database you are going to use, then develop a simple, direct plan that creates an explicit, formal structure. In other words, get out a pen and paper and start working out a mud-map of how you're going to get from point A to point B and beyond with this. :)

1 Data> 2 Database> 3 ?

... and so on.

In other words, what data are you going use? Gather it together. What database are you going to need? Get familiar with it. How do you need to manage the data once it's in the database? Get it in to the database in a way that it will be accessible and functional for what you plan to do with it down the track. Once it's in the database, how is your website going to access it? (How do you link the database with the webpage?). Etc.

Good luck.

PS: Thinking about this, if you know how to put together a web page and you know how to get data into a database, you may not need help with programming anything. It is probably just a matter of linking the right data with the right boxes on the webpage. :-k

It would help if you could further develop your idea with a visual representation of the project from raw data to webpage so we have a better idea (and so do you). :)

---

### Post by lisati on 2015-09-14
You might want to take a look at the [Programming Guides and Basics]("http://ubuntuforums.org/showthread.php?t=1766253") sticky in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section of the forum. If you'd like this discussion moved to that section, one of the forum staff can move it there for you.

---

### Post by isaiah4 on 2015-09-14
thanks for all the advice!  i appreciate it.
i thought i explained how i want it to be fairly well though.
i'll simply explain it again.
i want a user to see something like:
Age: ___
Height: ___
Weight: ___
Body Mass Index: ___
etc.

then they enter their information, and are shown results listing all of the nutrients they need, how many they need, and how frequently they need them.
i would also like there to be a list of foods with the nutrients they need including how many of each nutrient each food product has per x quantity (ex: 1 apple - x grams of fiber)
then they can select as many ingredients as they want and will be shown a total of all the nutrients the foods have together (ex, 1 apple, 1 banana, 1 orange - total of grams of vitamin C, x grams of vitamin A, etc.)
then they can be shown a list of recipes including some of their selected ingredients, maybe ordered by recipes including the highest number of ingredients first.  (ex: summer salad - spinach, tomato, etc.) and the recipes can include total nutrient values as well

another idea i had is for the program to tell you when you have enough nutrients from the food selected, as well as too few and too many by colors.  like if you need more of a nutrient the total will be yellow, when you have enough the total is green, and too many the total is red.  

everybody should have access to this kind of program, and i'm amazed it doesn't exist yet.  i want it to be free, so hopefully i can learn to develop it or get some free help making it.
thanks again for any advice

---

### Post by TheFu on 2015-09-14
Thanks for the explanation.  Nothing hard in this, just lots of details.  
In order to program something like this, you have to know exactly how to do it manually, on a piece of paper first.  

You might want to look at "NUT" which has all the USDA nutrition information.
[http://freecode.com/projects/nut](http://freecode.com/projects/nut) Perhaps forking that code would make sense?  It is GPL and written in C/C++ - those are harder to learn than Python, but leveraging what has already been done would probably save a year of development for 1 person.  [http://nut.sourceforge.net/](http://nut.sourceforge.net/) has more. "Stand on the shoulders of giants."

---

### Post by isaiah4 on 2015-09-14
thanks!
can you explain why i'd need to know C++ to make use of their information?
i really would like to use a program designed for making software without the use of coding... kind of like how some website makers let you make websites without knowing html.   does anything like that exist?

---

### Post by TheFu on 2015-09-14
Well, perhaps you are smarter about computers than I am and can find a way to leverage the code already written in C++ from some other language. At a minimum, you'd need to wrap all the C++ class methods into static functions, then wrap those into C calls so python can call those APIs. C is the standard for calling functions from one language to another. Every C++ compiler uses completely different calling object structures, so even different compilers can't link C++ libraries from different vendors.  C libraries on a platform are portable and can be called by almost any language - Ruby, Perl, Python, Java and probably any other language you care to method can call C libraries - no issue.

I suspect that explanation didn't help.

Sure, you can use the database, but NUT has already written code to track nutrition information and create recipes based on what foods are available. Wouldn't you want to leverage that?  To my knowledge, there isn't any drag-n-drop solution to do it plus any drag-n-drop solution wouldn't be able to link with C++ libraries anyway.

BTW "html" is not code. It is layout.  Apples/Oranges.  Perhaps you could make something like this drag-n-drop builder?  I know visual basic has something like that and Delphi did too. Those don't run on linux, last time I checked. Even with the d-n-d, lots of code has to be written to connect each "widget".

I suspect you get getting the idea that this is more effort than you want to attempt.  For someone with the correct skills, I'd guess it is about 2 months - if they leverage the NUT code - to get a mostly working program.  A cheap programmer would be $10K/month - the rates I've seen start at $75/hr for short-term efforts like this, but let's assume you can talk them down to a cheaper rate.

If the programmer you hire doesnt leverage NUT, it is probably 15 months of effort.

These are wild guesses.  I didn't sit down like I would for a real contract effort to map out the requirements, design, coding, testing, and documentation levels of effort.  Just remember that programmers are all optimists.  As a programming team lead, I learned to triple whatever my guys approximated for how long something would really take. Plus that estimate was after I gave them a list of what things were required - testing, documentation, bug fixing for 3+ weeks, stuff like that which developers always forget.  We'd go with their now "bloated" schedule and they'd come to me sooner and sooner into each project as it became clear they weren't going to meet their own deadlines.  
Fortunately, I'd told upper management what I was doing, so we all used the developer's schedules and made a big deal about missed deadlines.  Keeping the Marketing guys from screwing everything over was hard, however.  

There is a big difference between something that works and something that can be given to end-users - about 85% of all code is for that 2nd group. That's were all the bugs happen.  We have a saying .... "I made my code idiot-proof, but God keeps making better idiots."  Not very nice and quality code should never break, regardless of what anyone can enter into the program. NEVER.

If this is a web-app - be certain to follow the OWASP Top 10 list of vulnerabilities 
  [https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)

Make sense?

---

### Post by brian-mccumber on 2015-09-14
If you want to use a db and have this in a webpage online a php/mysql backend with a bootstrap frontend combo would probably be good for this and would work and look good across any device that uses a browser and c++ can be ported to php fairly easily if you follow TheFu's advice and use an existing library to save you some time developing it.

---

### Post by isaiah4 on 2015-09-14
Thanks for the replies.  Definitely becoming a more complicated project than I thought it would be.  
Why in the world haven't any software developers made an easy-to-use software developing program?
Do they maybe want it to stay so only the pros get payed ridiculous amounts for any software to be made? 
Oh how greed gets in the way of progress... haha.
Maybe I'll spend the months to learn and design the program but it sure would be nice to get help from a pro wanting to volunteer their efforts to make the program I want made.  It seems like a program literally every person should have access to, so should inspire a volunteer or two to want to help.

---

### Post by brian-mccumber on 2015-09-15
Not all software devs are greedy, what about the open source devs that bust their humps so you can use their operating systems and free programs? Devs have spent many years learning a language that is not easy for humans to understand so they should be paid well for their efforts. Volunteering for a full time job is hard to do because that doesn't make money to buy groceries and pay the light bill. What were your intentions for this app after it is made? Were you planning on trying to sell it to people or were you just going to put it somewhere so people could access it for free like open source software? And one more thing, are you qualified to be giving people nutritional advice in the first place?

---

### Post by isaiah4 on 2015-09-15
I guess you make a good argument.  Why don't they make programming simpler though?  Why can't they do for software design the same thing they did for web design?  instead of writing html you can use a program to easily put websites together, so why not the same thing for software?

Also I didn't think the software I wanted would take so much effort to make.  I thought if somebody knew what they were doing it could be made in a day or two, but I haven't written code or made any software before.

My intentions for the app was to have it accessible for free on as many sources as possible, like a website, on all app stores, and any other popular ways of accessing apps.  I may want to add advertisements to help pay for a domain fees but otherwise it was not a scheme to make money with.

---

### Post by brian-mccumber on 2015-09-15
So have you went to school for some nutritional science degree? What are you basing your formulas for deciding what people should eat on after their information is entered? I mean I can't help like full time or anything but if you can convince me you know what your talking about and aren't some quack that is just going to mess people up, I would possibly be able to give you a hand here and there.

P.S. WYSIWYG html editors blow. I have tried using them in the past, even Dreamweaver, and I was always in code view fixing the mangled mess that they made. So now I use a text editor and I write my own stuff using bootstrap as a framework.

---

### Post by isaiah4 on 2015-09-15
i have had a nutrition class in college, but i was planning on doing a lot of research to get all of the answers.  i may also call and/or visit a professional nutritionist to get any answers i can't find from reliable sources.  i imagine all of the information is already out there on the internet, but what i want to do is compile it all into a single organized source so it's easy for people to learn what they need without spending hours researching.

also, i actually found a website that almost has all of what i imagined the software i want to make would have, but their results aren't as well organized as i want.  for example, their results list all of the nutrients you need and how much, but they don't say how frequently you need them.  i also like the idea of allowing users to make a list of ingredients they want (as there are many different ingredients with the same nutrients) and display the total nutrients all of the ingredients have together.  

i'd definitely appreciate any help you want to be.  would you maybe be able to make the software if i provide all of the information?  honestly the software can be pretty basic as long as it is able to somehow list results accurately based on all of the user-input information.

---

