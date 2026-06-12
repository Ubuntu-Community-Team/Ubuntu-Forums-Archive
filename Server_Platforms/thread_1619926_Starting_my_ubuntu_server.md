---
title: "Starting my ubuntu server"
date: 2010-11-12
forum: Server Platforms
---

### Post by joacopaz on 2010-11-12
I have found a quite insightfull tutorial to aid me in the enterprise that is starting a brand new server with ubuntu. The thing that worries me is, once I set it all up (in my desktop computer), correct me if Im wrong:

I will have to design the website in another pc (my laptop) and then upload it to the ubuntu computer that works as server. This I am fine with, since the pages themselves are quite light to transfer, but the problem starts when i want to start a page (using the ubunto pc as server) that stores videos (avi) and music (mp3), and having people rate the music, while also having a user database (with passwords). How can I have people upload the files to the Ubuntu server and the user database working, how do I acomplish all of this without a GUI in the ubuntu computer? Should I design all in my laptop, and then upload it to the ubuntu pc?

I know my querry is quite a handfull, from designing the database to work to how to have third parties upload files, but any tutorial, direction or help i can get will be greatly appreciated.

Thanks in advance

---

### Post by Z.K. on 2010-11-12
> **joacopaz said:**
> I have found a quite insightfull tutorial to aid me in the enterprise that is starting a brand new server with ubuntu. The thing that worries me is, once I set it all up (in my desktop computer), correct me if Im wrong:

I will have to design the website in another pc (my laptop) and then upload it to the ubuntu computer that works as server. This I am fine with, since the pages themselves are quite light to transfer, but the problem starts when i want to start a page (using the ubunto pc as server) that stores videos (avi) and music (mp3), and having people rate the music, while also having a user database (with passwords). How can I have people upload the files to the Ubuntu server and the user database working, how do I acomplish all of this without a GUI in the ubuntu computer? Should I design all in my laptop, and then upload it to the ubuntu pc?

I know my querry is quite a handfull, from designing the database to work to how to have third parties upload files, but any tutorial, direction or help i can get will be greatly appreciated.

Thanks in advance



Well, you probably need to use an ftp system combined with a web interface and apache server with mysql or some other database to store your information in.

Learning SQL is not all that hard though I have never done anything on large scale.  You probably also learn php scripting or some other scripting language.  It makes setting up an html page for what you are trying to do a lot easier.  I took a few classes, but I am hardly an expert.  I just know some of the steps you need to do.  Then of course you need to lock down your system so you don't get hacked by some moron who thinks it is fun to break into someone's system and trash all their data.

There are quite a lot of tutorials around though on how to do this and look in the Ubuntu forums as they are quite helpful. If you do a search on the areas you need to learn, I am sure you can come up with some good discussions which probably have links to a good tutorial or you can just use google.

I have worked a little with some of this, but not enough to help you very much.  Anyway, good luck.

:P

---

