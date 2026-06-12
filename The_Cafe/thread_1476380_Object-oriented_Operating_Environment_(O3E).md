---
title: "Object-oriented Operating Environment (O3E)"
date: 2010-05-07
forum: The Cafe
---

### Post by Ioky on 2010-05-07
Here is a Operating / Desktop Environment concept I come up a while ago. I personally wouldn't have the time to develop it into reality. As currently going to Art School and student Architecture. And so do hell lot of un-related things. I would like to share this with people who might be interested, or anyone who willing to take a look. It is just a draft with very poor written language. But I think the concept are there. If any code got written for this, I would love to make it open source. or just for the concept itself, though Don't know if it is possible. Without further words here it is


Object-oriented Operating Environment (O3E) 


O3E Mission:

	The concept of Object-oriented has been serve many years in the programming world. It makes programming much  more flexible and logical. Object-oriented Operating Environment bring these advantage up front to the user end. User can build &#8220;Application&#8221; exactly the way they needed it without need of programming knowledge. For the Application designer, they will finally just focus on the design of the &#8220;Application&#8221;, then they can easily distributed their &#8220;design&#8221; to their user.  With O3E, user will no longer need to launch a heavy &#8220;All in One&#8221; software in order to do something simple. Or Just have simple software doing one thing but nothing else,and ending up open millions software in order to get to the point they wanted. 

O3E Concept:

Functions Container-	
	In O3E, the idea of &#8220;Application&#8221; doesn't exist, the concept of &#8220;Application&#8221; will instead replace by another Concept known as &#8220;Functions Container&#8221;. Imagine a Functions Container is a box, and base on what functions you needed, you add the Objects that serve such function into the box. And then &#8220;link&#8221; some of these functions together, so they can work with each others. In an Operating Environment, this Functions Container will also serve as a launcher, a script file, which fire up all the functions you put into the container in the way and order you wanted. The layout, and the style of &#8220;Application&#8221; will also be handle by the functions Container Script just like how markup Language work. 

Functions Pool-
	Functions Pool can be understand as a super market, where you shop your function objects, as well as a storage where you put your own unique function objects. It is also where the Container Script links the function it looks for. 

The Unix Philosophy-
	Instant of make program small and doing one thing well, in O3E we make &#8220;function&#8221; small and doing one thing well. It actually make more sentence. Think of this way. How can you actually define a image viewer is just doing what it  should be doing and doing it well? Have many function should it have? How can you tell what is the basic need of the program? However, in the level of a single function. There issue is much easier to define. 

Function Over Loading-
	Just like in Object-oriented Programming, where function sometime got over load because the some function need to handle its just difference depended on their parameter they are working with. For instant, the next button in a image viewer is difference than a next button in a PDF viewer. However, if you are making a mix viewer, it would be stupid and redundant to put two next buttons. Therefore the word &#8220;next&#8221; in O3E is all a &#8220;job title&#8221;. Functions with the same Job Title will appear as a single object. Depended on the situation they are try to handle. It will automatically pick the right function that associated with the operating the user try to do. (See Example for more Detail)


Function hierarchy-
	Depend on how the script got written. Some Functions object can have a hierarchy over another.  The higher power Function Object is call the Parent Object. And the object who under his parent object is call the Child Object. Child Object will got terminate if the Parent Object got terminate. 

Function Linker-
	There are no restriction on Function Object being running alone. Although many function on its very root are addition or enhance functions for another function. Like the Stop function find in many music player is need by many people, however, it is not absolutely need in order to play music. There will be a Object call &#8220;Play Music&#8221; and all it do is play the music file you ask it to play, once it the file got play fully, it will stop. In order to make it stop playing in anytime. You will than need a &#8220;Stop Object&#8221; which allow you to stop anytime you want. However, you don't have a Play Object in order to have a Stop Object. O3E allows user just fire up the Stop Object. However, it wouldn't do anything unless some kind &#8220;Stand Alone-like&#8221; function show up. So if a &#8220;Play Music Object&#8221; shows up. After the &#8220;Music Stop Object&#8221;. The &#8220;Music Stop Object&#8221; than will Automatically link to the &#8220;Play Music Object&#8221;. In some other case. User can choose what to link. (See Example for more Detail)

Function Addition- 
	Function Addition concept allows the user to add functions in real time as they needed. For example. A person is looking at an image with the image viewer. And S/he decided S/he want to sent this image to her / his friends. Traditionally, S/he will start some kind of communication tool than select the image S/he would like to send, then hit Send. With O3E. Instead run a completely difference software. He can simple run a function call &#8220;Send To Object&#8221; which all it do is sent things from object it linked together to the location take the user enter. If the user need to do some kind of editing while S/he looking at the image. S/he can simply run &#8220;Image Edit Object&#8221;. And do the editing right away. 

Multi-Launch-
	Function Container not just serve as a launcher for the functions. It can also serve a launcher for &#8220;Application&#8221;, as much as the user decided. For user who usually doing the same step every time they turn on their OS. Such as start a music play, then start an Instant Massager, then a Browser, and finally a Writer. They can write a script that will launch all this &#8220;Functions Container Script&#8221; in the order they wanted. User can always select all the &#8220;Functions Container Script&#8221; and launch them at once. 

Idea of Widget- 
	Widget is an Stand alone small scale tools, which is design for a single job or purpose. Widget is a absolute stand alone object  which can't not link to other Widget or Application or other Function Objects. However, Widget can be make in a Set, which item in the Set can be enable or disable freely, and have the ability to communicate to each others. Widget can have any kind of Graphical Skin, and they are Graphical only. They cannot be a command based function object. Except that they can be lunch in command line. 

Object: 

	Objects is what make O3E functional. Everything is an file, we call Objects, which is written to serve &#8220;ONE&#8221; function. NOT, in the sense of Alchemy, where &#8220;ONE is ALL, and ALL in ONE&#8221;, But &#8220;ONE&#8221; very specific purpose. 

	Adjustive is useful, in creating Function Object, It help to focus and narrow down the purpose of the Object. For example. Just use the word &#8220;Browser&#8221; for an Object would be too universal. It can mean any kind of browser. &#8220;Image Browser&#8221;would be more O3E. In some case. Like &#8220;Web Browser&#8221; is traditionally understand as the whole entire Application, but in a logical sense it is just the area where people actually see the website. Therefore. Using &#8220;Web Browser&#8221; would be perfectly fine. Although, And base on what render-engine is using. It could be even more specific. 

	- Objects much have Graphical and Command based interface to user if they are in anyway interact with user direction like give output to taking input. Except in the case that it is impossible to one but not the other. This kind of Object is also call a Stand Alone Object. 

	- Object that give support or enhancement to Stand Alone Object is call &#8220;reaction / Accessories Function Object&#8221; they sometime only exist in Graphical form, and sometime only exist in command line form. 

	- Object that simply run, and get something done  when order is given and stop, when stop command has been access is call &#8220;Prue Function Object&#8221;Sometime, they can be just be in back ground, as well. 

Example #1:

	Let's say, we to to design a very basic and typical Image viewer in O3E. We will need a Windows Object, an Image Browser Object, a Tool Box Object, and a Image Navigation Tool Set&#8221; Let's go through each Object one by one. 

	The Windows Object traditionally is the manager to handle all the application's position, and their focus. In O3E, it act more just like a display box, where things come in a set and nicely displayed. If you want. You can actually take everything out of the box, and put them anyway, as long as the designer allow you to do so. Even if they don't, you can hack it, simply by changing some parameter in the Function Container Script, although things much get a little bit out of control, but we think there is no reason for O3E to keep the free from the user. And of course, it come with all the traditional function that most of the windows manager has. 

	Browser Object is the actually &#8220;Display&#8221; for the image, which got loaded in. As what is it, its &#8220;Job Title&#8221; is Display, and can be combine with other &#8220;Display&#8221; for other contents. It is a &#8220;Stand Alone Object&#8221;, which mean its' basic function can take input and give output directly from the user, and interact with user directly. It loads the image, and display it on the screen with the original size. The User however, can use the scroll button to enlarge or reduce the size of the image (NOT Zooming). The reason this is not a separates function because it is part of the &#8220;Composition Concept&#8221; in O3E, which stand for All Function Object which can be visualize to end user is under the &#8220;Law of O3E Physic&#8221;. All Visualized Object can be MOVE freely in 3D-like-2D logic. In order word, they it move up and down, left and right. Front and back. Can go in front of each other. (User can enable True Visual 3D Composition) Enlarging is like bring the image closer to the User Visually. Which is difference that Zoom, which is Zooming into a specific area, within a fixed area that is equal to the original size of the frame of view. All Word should be chosen very carefully to define their name and function. 

	The Tool Box Object, is a Box who can group tools set item together can lock them in place. So the User can move all the tools in the set all at once. Tools box can hold nothing but Object that has the job title &#8220;Tool&#8221;. In the &#8220;Image Navigation Tool Set&#8221;, there is Tool Objects that give the basic Navigation  function to view the Image in the Image browser, such as next, previous, zoom in, zoom out, Rotating, and flipping. Just Image how would you physically looking into a image.(Note: Not how you can actually do with the media that hold the image. Twisting it,  rolling it, and whatever crazy thing you might thing of.) However, no one say you can't do it. Just that you might need to write the function yourself. 

	Once we put all this elements in a layout format into the Script, the &#8220;Application&#8221; is really to go. Known it. All the Object we use is actually under the &#8220;Image Class&#8221;, and they are specifically written for handling image. If things goes like this, everything you try to do with have their own function that do actually the same things. To the user might be, but in the coding level it is totally different. A Save button, is totally writing differently in a writer application, than a image editor. That is why we give each object a &#8220;Job Title&#8221; so they can appear the same to the end user. If. A Function Object is truly exactly the same in two &#8220;Class&#8221;. They will simply be a one located somewhere, while the other one is just &#8220;Symbolic linked&#8221; to the actual function. So when the user looking for Function Object in the Class, they will still see it in the class. Once again it is pretty much like OOP just that everything have bring up front to the user. 

	You might ask, why can't be the browser just be a one universal browser that can open everything you through into it. Well they, You can call a &#8220;Bowser&#8221; is just an Object that Open things. But in the coding level. Programming will need all the libs in order for the &#8220;Universal Browser&#8221; be able to Open everything it through at it. In a way, It is impossible to make a browser that have that ability without take all your computing powers, because there are simply too much format out there. That is why Function should be giving a very specific focus. Objects in O3E is not trying to be &#8220;GOD-Like&#8221; but a &#8220;Great Part&#8221; of the Whole.

---

