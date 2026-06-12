---
title: "UML diagrams and free software"
date: 2007-02-26
forum: The Cafe
---

### Post by vadania on 2007-02-26
I am questioning myself why Unified Modelling Language is not used for free software development? I haven't heard of any free software project that uses any UML tehnology, although there are several UML tools under the GPL licence. 

Why is that?
Why do you think free software developers choose not to use UML?
Do you think it has to do with legal or technical problems?

Is the UML standard itself under a weird non free licence?
Or that they find no software development methodology usable for free software development (from both legal and technical point of view)?

Please share your vision on this matter with me, or point me to a forum / other resource where this can be discussed.

---

### Post by YourSurrogateGod on 2007-02-26
UMLs are simply a way to develop software (which is simply one part of the development process of any software.) After the software is developed and works, no one really bothers with UML.

---

### Post by punkinside on 2007-02-26
I don't know why open source devs don't like UML, I think it would be nice if alongside the source code (which can be a real pain to read) they included a couple of UML class diagrams or at least sequence diagrams so that a third party could understand the code much quicker. 

I guess they just don't care who reads their code or if anybody but themselves understand it. I know documentation is a pain, if I were given a chance not to document any of my work, I certainly wouldn't (at least as thoroughly)

---

### Post by Luggy on 2007-02-26
double post wooo

---

### Post by Luggy on 2007-02-26
[Dia: A UML generator]("http://www.gnome.org/projects/dia/")

Dia is pretty cool, there are a bunch of plugins that will generate code from your diagrams. I haven't used them though.


I think the reason why many devs don't use UML is because there are other tools out there that are just as good but take less time. [ Doxygen]("http://www.stack.nl/~dimitri/doxygen/") is a great example. Instead of generating a UML diagram, you start writing code and it can generate all the documentation needed.

I took UML in school, but when I have to start work on something, I rarely create a UML diagram. I might use Dia for getting the thoughts straight in my head but I don't use it for communicating within a team. There are other, better techniques out there.

---

### Post by punkinside on 2007-02-26
Like what? I find that a UML session before going to work gets pretty much all of the team on the same page and greatly improves output. But mind that what I'm talking about is using UML on whiteboards to understand the problem rather than to document.

---

### Post by ZylGadis on 2007-02-26
FLOSS developers are enthusiasts. They rarely work in teams (as in meetings every day, etc), because they are well aware that business-level teamwork is something that happens in corporations because the employees there are either not smart, or not interested, or both. You don't need a UML diagram in order to understand someone's code if you know what you are doing, and you are interested, and the code is well-written.

In short, UML is a very business thing, and does not belong where true work is being done. UML is a waste of time - that time can be spent much better.

---

### Post by punkinside on 2007-02-27
> **ZylGadis said:**
> FLOSS developers are enthusiasts. They rarely work in teams (as in meetings every day, etc), because they are well aware that business-level teamwork is something that happens in corporations because the employees there are either not smart, or not interested, or both. You don't need a UML diagram in order to understand someone's code if you know what you are doing, and you are interested, and the code is well-written.

In short, UML is a very business thing, and does not belong where true work is being done. UML is a waste of time - that time can be spent much better.

Hmmm I never thought that designing and coding a stable, secure multiple layer system that controls everything from the payroll, ordering, shipping up to the finances of an organization was not true work. Here I was thinking that managing requirements, writing use cases and drawing class and sequence diagrams was actually helpful to understand a problem domain. Silly me.

Good luck trying to scratch the surface of more than 500,000 lines of code without some sort of documentation. But hey, if I work in the business thing, I must not be that smart.

---

### Post by Luggy on 2007-02-27
I think what was tried to be implied with the previous post was that the development teams for many FLOSS projects tend to be smaller and all those involved are usually of the same level of understanding. My work generally follows this catagory; we have a small team with only a few coders and very short deadlines. Spending the time creating fancy UML diagrams would be nice, but it's not that effective for our design team. Using Doxygen to document our code and create the API is a much better for our team.

If you are talking about creating a huge system that will effect everyone in a large organization then any sort of diagraming will be useful, and UML with it's actors and use cases can be very effective. I am using dia to create the database diagrams for our one project right now.

---

### Post by punkinside on 2007-02-27
> **Luggy said:**
> I think what was tried to be implied with the previous post was that the development teams for many FLOSS projects tend to be smaller and all those involved are usually of the same level of understanding. 

I know that. I've worked in small groups before, and still have a little thing on the side with a couple of friends. I still think its a good practice to at least sketch a bit before writing code. In all but the most trivial of cases. 

What I did not care for is calling people who work for corporations dumb or uninterested, and calling the work being done not "true" work.

> **Luggy said:**
> 
My work generally follows this catagory; we have a small team with only a few coders and very short deadlines. Spending the time creating fancy UML diagrams would be nice, but it's not that effective for our design team. Using Doxygen to document our code and create the API is a much better for our team.

The post I made was not about documenting *per se*. Like I said earlier, simply sketching on a whiteboard and discussing the design for a bit before coding can help afterwards, making the code cleaner and more direct cause you know exactly where you're going.

 > **Luggy said:**
> I am using dia to create the database diagrams for our one project right now.

I like dia, I use it for most of  the projects we get at the university. Good app, but it can be temperamental at times. At least the version that was in the dapper repos. I haven't used the one in edgy enough though.

---

### Post by Tomosaur on 2007-02-27
It's because software developers generally aren't software engineers. The software engineer uses UML diagrams and other design tools - the software developer just writes the code. Many open source projects lack software engineers - and design is done alongside the development rather than prior to it. Universities and colleges tend to teach some software engineering skills to software developers - even though the responsibilities of the two groups are very different. In the same way, software engineers need to know how to create rudimentary code, because it allows prototypes to be created very quickly. 

Many open source projects lack software engineers, because software engineers need to be assigned to a project before they can use their skills. Hence - FOSS projects tend to attract very few software engineers, which is one of the reasons too many FOSS projects fail, or provide too many, or too few, features. It's the responsibility of the software engineer to say 'this is what this application needs'. A software developer who knows about software engineering can at least direct a project, and set out a development model, even if they're not qualified software engineers.

---

### Post by runningwithscissors on 2007-02-27
> **vadania said:**
> I am questioning myself why Unified Modelling Language is not used for free software development? I haven't heard of any free software project that uses any UML tehnology, although there are several UML tools under the GPL licence. 
Because from a development point of view it is pretty much worthless. Programs need to be defined down to the last detail to form a correct model, which most developers agree, is something that never happens.

> **vadania said:**
> Why is that?
Why do you think free software developers choose not to use UML?
Do you think it has to do with legal or technical problems?

Is the UML standard itself under a weird non free licence?
Or that they find no software development methodology usable for free software development (from both legal and technical point of view)?
They don't see much point to using it. It is a community where actual code is valued, not abstract models and ideas.

> **vadania said:**
> Please share your vision on this matter with me, or point me to a forum / other resource where this can be discussed.
Well, in my "vision", UML is useless. I don't see the point of it, for the reasons stated above.

---

### Post by punkinside on 2007-02-27
> **runningwithscissors said:**
> Because from a development point of view it is pretty much worthless. Programs need to be defined down to the last detail to form a correct model, which most developers agree, is something that never happens.

I also agree. Have you heard of the [Rational Unified Process]("http://en.wikipedia.org/wiki/Rational_Unified_Process")? One must always take into account changing requirements and realize one can never completely define the solution beforehand. But a class diagram helps a lot to understand the problem domain, use case writing and diagrams are specially apt at defining what the software should do and sequence diagrams are very helpful when it comes to designing interaction between software objects. I'm studying CS and specializing in software engineering but work as a developer most of the time (I'm not even graduated yet). In my experience, trying to at least model the problem domain, and refining it iteratively, can greatly improve the chances of success of a project.

> **runningwithscissors said:**
> 
They don't see much point to using it. It is a community where actual code is valued, not abstract models and ideas.

Code comes from abstract models and ideas, wether you set them on paper or not. And actual code can be very much worthless and/or inefficient if those models are not properly represented. I'm just saying that thinking about it a little bit before writing code is most definetely a good practice no matter what the project is. And use of UML encourages that.

> **runningwithscissors said:**
> 
Well, in my "vision", UML is useless. I don't see the point of it, for the reasons stated above.

Well, you're entitled to your vision. I'm entitled to disagree :)

---

### Post by ZylGadis on 2007-02-27
> **punkinside said:**
> Hmmm I never thought that designing and coding a stable, secure multiple layer system that controls everything from the payroll, ordering, shipping up to the finances of an organization was not true work. Here I was thinking that managing requirements, writing use cases and drawing class and sequence diagrams was actually helpful to understand a problem domain. Silly me.

Ever looked at the code of such a thing? I have. Silly you indeed.

High-quality work is only done by smart/knowledgeable AND interested people. It is nearly impossible to find the combination in a corporation, and if you do, the poor competent person is usually drowned by the throng of dullards. Been there, done that. No, thanks. I'll take a dumb / leisurely job to pay the bills, and do FLOSS in my spare time, any day.

I'll reiterate that for all practical purposes, when code is done right, UML is next to useless. It is not completely useless, but your time (as a competent developer as opposed to some parasite whose job is to order others around) is much better spent doing other things.

---

### Post by Bagboy23 on 2007-02-27
UML is a modelling tool which is part of systems analysis. In open-source software development, there is no "real" functional/non-functional requirements as development is primarily done via creativity and only limited to what developers what to achieve. They can basically do what they want; when they want. Additionally, the open-source movement does not have clients; but a large group of a community which it hopes it will cater for; if it doesn&#8217;t cater for the community; i.e. a simple function is missing, the open-source developers won&#8217;t make a big fuss about it and MAY include it in a future release &#8211; again if they want to; it&#8217;s exclusively at their judgment.

In a corporate environment we have clients who pay for a business solutions and they want what they paid for. 

As a consultant myself, we have to use UML in a business environment not just for understanding business processes or processes in general but to model the entire business and map functional/non-functional requirements. The reason is simple; a client like Ford Motors understands their business clearly. We're not there to re-engineer their existing business processes or devise strategic business solutions or to even preach to them purely because they know what they&#8217;re doing; hence consultants are brought in to implement technology to meet business requirements. This is when UML modelling and methodologies like RAD, DSDM, AIM come in use. In large projects where you have a few hundred people working on an implementation, you need structure, organisation and management. This is where things like modelling, methods and methodologies help. Without them it would be impossible to collaborate on global projects.

Also, don't confuse the usage of UML and methodologies in personal projects or medium sized projects such as writing a web application or developing a database for a small company; systems analysis is almost always done at corporate level to minimise on risk, after all it's not about what you think works well but what suits the clients needs.

---

### Post by ZylGadis on 2007-02-27
Spot on. I'll simplify it like this: if money, and not quality, is the driving force, then all kinds of actions take place that are fundamentally unnecessary otherwise. Corporations are all about money -> they use UML, Rational Rose, etc. FLOSS is all about quality - no time is spent on the above.

---

### Post by punkinside on 2007-02-27
> **ZylGadis said:**
> Ever looked at the code of such a thing? I have. Silly you indeed.


I'm writing code to add some features to one of those systems now. Whats your point? Should I have wasted a day looking at the classes and figuring out the call order and thread management when I found out what methods I had to override and in which classes in 5 minutes via a sequence diagram?

> **ZylGadis said:**
> 
High-quality work is only done by smart/knowledgeable AND interested people. It is nearly impossible to find the combination in a corporation, and if you do, the poor competent person is usually drowned by the throng of dullards. Been there, done that. No, thanks. 

Well, I'm sorry to hear you had a bad experience. Of course there are always dullards, and its a pain when they're your superior, mostly because they just end up making you do dumb things. Has happened to me. Solution: resign, get a better job. Easy. I'm quite happy where I am now.

> **ZylGadis said:**
> 
I'll take a dumb / leisurely job to pay the bills, and do FLOSS in my spare time, any day.


Well, its your life. I plan to do things quite a bit differently.

> **ZylGadis said:**
> 
I'll reiterate that for all practical purposes, when code is done right, UML is next to useless. It is not completely useless, but your time (as a competent developer as opposed to some parasite whose job is to order others around) is much better spent doing other things.

Like I said earlier. UML saved me a day of looking at code I didn't need to know. And I've said it once and again. I sure think documenting is a pain, but it makes life easier later, for everyone. And I find that trying to stop and *really* think about what you're going to do before doing it is just common sense to me.

---

### Post by Bagboy23 on 2007-02-27
Zy, no disrespect but unless you know how business management and corporate structure works, you&#8217;re never going to realise or understand concepts such as Faster ROI, lower TCO or any of the formal rational methods CIOs use to determine the feasibility and need of any IS and it&#8217;s important need for analysis. 

In simple terms; corporate implementations work like this; business case; plan, design, implement.

In open-source it&#8217;s simple as well; just write code.

These are two different scenarios completely and need to be looked at differently.

---

### Post by runningwithscissors on 2007-02-27
> **punkinside said:**
> I also agree. Have you heard of the [Rational Unified Process]("http://en.wikipedia.org/wiki/Rational_Unified_Process")? One must always take into account changing requirements and realize one can never completely define the solution beforehand. But a class diagram helps a lot to understand the problem domain, use case writing and diagrams are specially apt at defining what the software should do and sequence diagrams are very helpful when it comes to designing interaction between software objects. I'm studying CS and specializing in software engineering but work as a developer most of the time (I'm not even graduated yet). In my experience, trying to at least model the problem domain, and refining it iteratively, can greatly improve the chances of success of a project.
Designing software does not necessarily mean pigenholing software into UML form. UML is so far removed from development methods and tools, it's not funny. Ideally, it would work if software development had rigid and established methods of doing a particular job, but that is not the case. Contingency plans notwithstanding.

Yes, you can formulate nice little abstracted modules and establish their methods of interaction and behaviour. However, more often than not, the model you're looking to emulate is impacted by the tools you use to develop the software.
Libraries have their limitations, feature requests tend to violate abstraction rules between different modules, etc. etc.
Frankly, I'm amazed at how far certain people have managed to pull this UML lark.

> **punkinside said:**
> Code comes from abstract models and ideas, wether you set them on paper or not. And actual code can be very much worthless and/or inefficient if those models are not properly represented. I'm just saying that thinking about it a little bit before writing code is most definetely a good practice no matter what the project is. And use of UML encourages that.
Of course you ought to have a rudimentary design and plan before beginning development. But codifying that plan into a formal UML model is more trouble than it is worth. Hey, great for those who make a living off it. I don't begrudge them that. However, I am not convinced of the usefulness of such a model. I've only ever found it to be a rather rigid stumbling block towards actual development.

> **punkinside said:**
> Well, you're entitled to your vision. I'm entitled to disagree :)
Fair enough.

---

### Post by punkinside on 2007-02-27
> **Bagboy23 said:**
> UML is a modelling tool which is part of systems analysis. In open-source software development, there is no "real" functional/non-functional requirements as development is primarily done via creativity and only limited to what developers what to achieve. They can basically do what they want; when they want. Additionally, the open-source movement does not have clients; but a large group of a community which it hopes it will cater for; if it doesn’t cater for the community; i.e. a simple function is missing, the open-source developers won’t make a big fuss about it and MAY include it in a future release – again if they want to; it’s exclusively at their judgment.

In a corporate environment we have clients who pay for a business solutions and they want what they paid for. 

As a consultant myself, we have to use UML in a business environment not just for understanding business processes or processes in general but to model the entire business and map functional/non-functional requirements. The reason is simple; a client like Ford Motors understands their business clearly. We're not there to re-engineer their existing business processes or devise strategic business solutions or to even preach to them purely because they know what they’re doing; hence consultants are brought in to implement technology to meet business requirements. This is when UML modelling and methodologies like RAD, DSDM, AIM come in use. In large projects where you have a few hundred people working on an implementation, you need structure, organisation and management. This is where things like modelling, methods and methodologies help. Without them it would be impossible to collaborate on global projects.

Also, don't confuse the usage of UML and methodologies in personal projects or medium sized projects such as writing a web application or developing a database for a small company; systems analysis is almost always done at corporate level to minimise on risk, after all it's not about what you think works well but what suits the clients needs.

Perfectly said. But why is it so hard to understand that UML can actually help in smaller projects as well?

> **ZylGadis said:**
> Spot on. I'll simplify it like this: if money, and not quality, is the driving force, then all kinds of actions take place that are fundamentally unnecessary otherwise. Corporations are all about money -> they use UML, Rational Rose, etc. FLOSS is all about quality - no time is spent on the above.

Well, clients pay money for quality. Or do you think that sotware that runs critical business processes for a big company can afford to be without quality?

FOSS developers have the luxury of doing a crappy job, after all, they do what they want, when they want it, and nobody is expecting anything from them. Bigger software projects where real money is at stake don't have that luxury.

---

### Post by punkinside on 2007-02-27
> **runningwithscissors said:**
>  UML is so far removed from development methods and tools, it's not funny. 

Why do you say that? I've used my share of CASE tools, some very good. And many have the option to generate code which most of the times is perfectly adequate way to start off development.

> **runningwithscissors said:**
>  
Ideally, it would work if software development had rigid and established methods of doing a particular job, but that is not the case. Contingency plans notwithstanding.

Thats what [Design Patterns]("http://en.wikipedia.org/wiki/Design_Patterns") are for.

---

### Post by Bagboy23 on 2007-02-27
Sorry I should be clear. When I said small project I was thinking of small projects with a group of 3 - 4 people. Mainly a group of friends who understand one another. However, if we're talking about 3 - 4 people who do not understand one another then UML and methodologies provide the standardisation.

I think it's important to understand that rarely does UML exist alone; rather it is always part of a methodology. 

The dispute regarding the value of UML in projects may be due to some confusion depending on the types of project people are working under. For instance, I could easily work with my friends (a group of 10) without using modelling or methodologies primarily because we all followed a similar project structure. Now this may be the case for a lot of other people here. They may be focused on their small projects thus providing arguments on this basis. However, my project with a large Fortune 500 firm consisted of over several hundred people working on the implementation which **required** a methodology and UML for maintaining standardisation and understanding throughout the entire project.

---

### Post by ZylGadis on 2007-02-27
I am currently doing a PhD in SE (actually Analysis, but it's under the SE hat). I have been through Rational, Structured, XP, and all kinds of other acronyms. I have come to the conclusion that corporations are really only driven by money, and they are willing to trample all other parameters in the equation in order to get that money. Some of those parameters are more important than money to me.
I understand there was no disrespect intended, as you did not know my background. It is simply a matter of different goals - different value systems, if you will. I find that quality code is produced only when quality code is intended. Money just gets in the way.

---

### Post by Bagboy23 on 2007-02-27
Just to add; UML and software development methodologies aren&#8217;t excusive to corporate firms. Many charitable organisations and community projects implement modelling techniques and methods to manage their projects as well. Rather than focus of Class Diagrams and sequence diagrams at a lower-level, there are higher-level modelling techniques such as use cases and other modelling techniques such as conceptual modelling that is heavily adopted by corporate firm or otherwise. In short; UML and it&#8217;s counterparts provide the flexibility and structure that many projects need.

It&#8217;s not my place to judge you on your opinion about corporate firms; but being an academic you should have some understanding of how the economy works and the need for corporate firms. However, this is a discussion for another time.

---

### Post by vadania on 2007-02-27
Sorry. I tried to edit my post and I was playing with back and forward browser buttons.

---

### Post by vadania on 2007-02-27
Some members say UML is unuseful or of little use for free software developers / small projects. The others: please do not argue with the first category
 
 I belive UML can be useful for designing gpl software, but I will not give arguements supporting my judgment as I do not seek to prove anything here. Nobody has to convince anybody of anything and in this thread I am not trying to market out the idea of using UML.
 The purpose of this thread is to get feedback about what you do not like regarding the way UML tools work.  I plan to use this feedback to make a tool that makes free software development with UML a little easier.
 
 From your input and what I learnt, I understand using UML for designing GPL software has the following problems: (Order is not important)
  1 developers never actually meet users or each other - except for the conferences 
  2 UML is too complex;
  3 takes too much development time;
  4 not all team members know UML; 
  5 most free software developer teams do not have software engineers
 
Could you find other problems with UML diagrams and free software? Please share them. Yet, I am not interested on finding ways to solve these problems. That will be a future task.
 

UPDATE: As a closing thought, I find the biggest problem with using UML for developing GPL software is the lack of a clear developing method and the tools that work with distributed development. The other problems can be overcome, I think.

---

### Post by Vevmesteren on 2007-03-04
when creating structures for new web apps that I plan I always plan them out in a diagram. Breaking down the class and data structure visually helps me a lot. What I loved about this was that once I was happy with the structure I could, with a feww simple clicks, convert my visual structure into the classes with all Parameters, functions and the works predefined. So now I have created my class structure in DIA just to realize that I cannot export it. Or well I cannot see how to export it. I do see that there is a Python code generation export, it is almost in the lines that I would like. But what I really whant is an XMI export feature. Is that too much to ask from poor ol' DIA. Or maybe there is some nifty way of converting the generated Python code to an XMI sheet? Anyway....any help would be greatly appreciated...

thanks

V

---

### Post by vadania on 2007-06-04
I read some time ago exporting from DIA is possible if you install some additional packages.
Sorry, don't remember the link.

My opinion is we lack some wiki website where someone can sketch some diagrams without installing anything.
If it would store diagrams in XMI it would be effortless to export it.
It would fit nice between code documentation for developers (Javadoc, doxygen, ...) and user guide.

If I'm a new developer i would understand much better from a SVG sketch than from an ASCII diagram:
see:

[_ _ _]
[client] --------> [_web server_] ----->[_database_]
[_ _ _] _ _ _ _ _ _ |_ _ _ _ _ _
_ _ _ _ _ _  [_file system_] _ _ _ _ _ _   

   (this is just a demo), LEGEND:_ _ _ _ _ _ is &&amp;nbsp; because whitespace formatting is not displayed well 

Explaining this in text is awful, some users are simply more visual. I belive users are like kids - "forget about the text just gimme the pictures'. I also belive this is the reason RTFM is still more at home with free software than with proprietary software (people read less free software documentation than for proprietary).
To support the idea that the visual is important for readers, i bring only this: Documentation readability improved a lot with the arrival of the documentation formating (bold, italic, headings). 

Also from the technical point of view, In ASCII it takes a lot of time to build this, not to mention updating...

My idea is this:

_version control system----------> XML XMI files  ----> XSLT transform them ---> XML SVG ---> Firefox
_ _ _ _ _ _| _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ __ _ _ _ _ _  | _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ _                    
_ _ _ _ _ _| _ _ _ _ _ _ _ _ _   (client side XSLT via JavaScript for editor users or server side for viewers)
_ _ _ _ _ _| _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ __ _ _ _ _ _  _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ _                    
_ _export XMI to 3rd party applications_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
    (for experts) _ _ _ _ _ _| _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ __ _ _ _ _ _  _ _ _ _ _ _ _ _ _ _ _
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ __ _ _ _ _ _  _ _ _ _ _ _ _ _ _ _ _ _ __ _ _ _ _ _     

Technical issues to develop such a software:
This is a website that transforms UML XMI to SVG: [URL="http://uml2svg.sourceforge.net/online/"]http://uml2svg.sourceforge.net/online/
[/URL].  You can also use their XSLT trasformation files for your own purpose, as uml2svg is a GPL project.

You also need a web XML editor, [http://bitfluxeditor.org/demo/]("http://bitfluxeditor.org/demo/") could be a start. The only problem remaining is I didn't find the wiki that should bind these programs together.


If  you start this kind of project please let me know. Until then, I' do the best I can to start it.
I'm also looking for developer advice (how to be a good developer).


NOTE: If you belive diagrams are not useful for free software developers, just ignore my opinion here.

---

### Post by DoctorMO on 2007-06-04
I don't know, I played around with UML for awhile but  I could never understand what all those fancy words mean that you need a computer science degree to understand.

I understand structure, I draw many diagrams and idea maps and various other things ina little black note book. I'm sure given the chance I'd find standardising on UML helpful. but unless someone says 'HERE a script to convert your perl or python code into a nice UML diagram to recover it and HEAD is a document to help you understand what the hell it all means'

Don't forget as an open source programmer I need to work from code to UML and back again depending on what motivations are going on and what stage of the idea is being explored. small teams without managers and requirements force this perspective.

Oh and I did read those interesting pasterns and anti-pasterns books; but for most of them you sort of go 'well duh' although perhaps for those 20% of methods you didn't know before it was usefull but took a lot of time.

---

### Post by vadania on 2007-06-04
You are talking about source code generation, and source code reengineering (transforming c++ into a diagram). This is supported by most expert tools on the market (Poseidon, Umbrello), do not know if they included this in the Community GPL edition or just in proprietary versions. Python and perl support could be easily be added to such expert tools.
Now I realise an important component of this modeling tool would be a strong version control system that serves XMI files to the wiki and those 3rd party tools (Eclipse, Netbeans, Umberello)

I am also a beginner with UML, I haven't read any pattern book yet.
However you could use only the UML diagrams you know about. I find useful the principle 'use simple things first, learn about the advanced later" and practice is just as important as theory.

---

### Post by RyanZec on 2008-03-07
I think designing UML diagram before coding is good if you have the time.  I use UML fo plan out my databases and personal php projects but only started being able to use it at work(we were always like we have no time).  however after you start coding mantaining that becomes an issue and the is where code documentation takes over(like phpdoc for php),

---

