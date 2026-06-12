---
title: "Talking about Ubuntu Studio with Scott Lavender, Project Lead for Ubuntu Studio"
date: 2010-08-12
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-08-12
*Have you ever wanted to know more about some of the Ubuntu derivative distributions? In this interview we look at Ubuntu Studio with [Scott Lavender]("https://wiki.ubuntu.com/ScottLavender") Ubuntu Member and Project Lead for the[ Ubuntu Studio Project]("http://ubuntustudio.org/").*

                                                                                                                                            [IMG]http://fridge.ubuntu.com/files/IMG_4896.jpg[/IMG] 

 
 
 
 
 ***Amber Graner:****** Scott can you tell readers a little about yourself and how long you have been involved with Ubuntu and Ubuntu Studio?***

 **Scott Lavender:** My name is Scott Lavender and I’m in my first release as the project lead for Ubuntu Studio.

 I got started with Ubuntu during [Feisty Fawn ]("https://wiki.ubuntu.com/Releases")in January of 2008 due to an article in PC Magazine. I usually don’t buy such magazines but the cover mentioned an article about using Linux, specifically Ubuntu.

 During Hardy I discovered Ubuntu Studio by accident and as a musician I was greatly intrigued by it. I spent the following year acquainting myself with the included applications and learning about Linux audio in general.

 I felt that Ubuntu Studio rocked so much (oi, that sounded Jono-ish) that I decided I wanted to give back by contributing to the project. So just over a year ago I introduced myself to the Ubuntu Studio team and began helping in any and every way I could.

 During that time Ubuntu Studio was suffering from attrition and a lack of distinct, active leadership. This isn’t to intimate that development was completely absent as several developers long associated with the project continued to work on core systems such as the audio stack. However, the project had lost focus and day-to-day activities were being neglected.

 Ubuntu Studio was too important to me to see it devolve and possibly die, therefore rationalizing that passionate, albeit inexperienced, leadership was better than no leadership, I offered my services, as they were, as project lead.

 ***AG:******For those readers who haven’t heard of Ubuntu Studio can you tell people what Ubuntu Studio is and how it differs from Ubuntu?***

 **SL:** Topically, Ubuntu Studio could be described as “a multimedia editing/creating flavor of Ubuntu.” That is how it is described on the wiki - [https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio).

 To be clearer and more substantive, it should be noted that Ubuntu Studio is based on Ubuntu and therefore share the same code and repositories. Any applications available in one is likewise available in the other.

 Ubuntu Studio begins to differ, however, with the selection of applications installed. As a multimedia flavor of Ubuntu we include a substantial amount of applications for audio, video and graphics that are not included in a vanilla Ubuntu installation.

 Additionally, there are significant, detailed configurations that are intended to improve performance. The most prominent example use case would be enabling real-time priorities for recording audio.

 Lastly, I would remiss if I failed to point out that since we start with the exact same code base, any problems experienced with hardware or applications in Ubuntu will also most likely be experienced in Ubuntu Studio, and vice versa.

 ***AG: ****** How many people are currently involved with developing Ubuntu Studio?***

 **SL:** Not many! Less than five people are actively and directly working on Ubuntu Studio at any given point. That number is probably closer to three at most times.

 Currently, we struggle to maintain the functional necessities like ISO testing and addressing bug reports given the availability of human resources. Aspects of the project like updating/maintaining the web site, improving documentation, community development, art and themes, and programming are being horribly neglected.

 At this point I would like to clear up the ugly misconception that someone must be a dynamic and experienced developer to help Ubuntu Studio. Only a modicum of general, common experience would suffice for most of our needs.

 Any help would be greatly appreciated. If you are interested in helping or want more information please see my [latest blog post]("http://dullass.blogspot.com/2010/08/state-of-ubuntu-studio-2010.html").

 ***AG: ******What are the biggest challenges you face in developing a derivative of Ubuntu? What type of funding if any do you have for this project?***

 **SL:** I feel that any challenges faced as a derivative of Ubuntu are small and inappreciable, especially in contrast to other challenges like the aforementioned lack of contributors and developers. Furthermore, I would note that the benefits as a Ubuntu derivative greatly outweigh any challenges experienced.

 At this time I am unaware of any monetary funding for this project. However, like other derivatives, we receive other support such as ISO image systems (building and hosting), ISO QA testing, and web site hosting.

 That being said, if monetary funding were made available to the project we would certainly find an appropriate and helpful use for it.

 ***AG:****** How easy is Ubuntu Studio for people who aren’t familiar with audio, video, and graphic design to learn and master? What do people need to know prior to using Ubuntu Studio?***

 **SL:** Hmmm&#8230;I view this as a tool versus art, learning versus mastering question. To answer this, I would like to establish a slightly alternate definition of Ubuntu Studio as a collection of applications installed in a multimedia configured operating system and as such, I consider Ubuntu Studio as a tool.

 Therefore, as a tool, Ubuntu Studio is not prohibitively difficult to learn assuming a minimal subset of prerequisites. Some of those prerequisites would include experience with a Linux system and a fundamental understanding of the preferred artistic medium. To exemplify, a proficient artist or musician familiar with Ubuntu would probably experience very little trouble creating art or music with Ubuntu Studio. In contrast, a Windows user bereft of artistic abilities would find it difficult to create either art or music in Ubuntu Studio.

 While I believe learning Ubuntu Studio and becoming proficient is readily assessable to most people, I do not think that mastery is likely. Without intending to sound like a Zen aphorism, has Blender been mastered yet by anyone? This is but one aspect of Ubuntu Studio.

 Prior to using Ubuntu Studio I would suggest that a user clearly identify what they intend to accomplish, determine the appropriate application(s)*, and then research that application to understand how its commands work. For example, if I wanted to record a live band I would probably determine that I need to use JACK and Ardour. I could then search for a tutorial that explains a typical use case.

 This may seem overly complicated, but painting a picture requires choosing the appropriate canvas, brushes, and pigments. Additionally, the proper knowledge of how to mix the pigments or different brush strokes may be required as well.

 * The following are good resources to determine which application is required: Ubuntu Studio’s [online documentation]("https://help.ubuntu.com/community/UbuntuStudio"), [Ubuntu Forums]("http://art.ubuntuforums.org/forumdisplay.php?f=335"), [mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users"), and IRC Channel #ubuntustudio on [freenode.net]("http://freenode.net/").

 ***AG:******Can you explain how Ubuntu Studio deals with questionable media codex (ie mp3, AAC, etc)? What is your policy in regards to these dealing with formats such as those?***

 **SL:** Ubuntu Studio ascribes to the same licensing policy as Ubuntu; proprietary formats are not shipped in the ISO images but are available in the repositories.

 ***AG:******Does the Ubuntu Studio project follow the same release schedule Ubuntu? If so, what can Ubuntu Studio users expect from Ubuntu Studio on 10.10.10?***

 **SL:** Ubuntu Studio does follow the same release schedule as Ubuntu.

 For 10.10.10 I believe users can expect appreciable progress in resolving integration between Pulse Audio and JACK (professional grade, low latency sound server) and the continued additions of LV2 plugins and applications.

 I wish I could be more definitive and explanatory about the Pulse Audio / JACK integration but much of this process is based on what happens upstream with Pulse Audio and Lennart Poettering.

 ***AG:******Since 2007 how has the project progressed and grown? What has been the most surprising and most rewarding advancement of the project to date?***

 **SL:** It is possible that I cannot properly answer this question since I’ve only been directly involved with the project for just over two years.

 However, while I have been involved I have see tremendous growth in terms of stability and usability. Given the nature of open source development, this did not occur without significant and sustained efforts.

 I think getting JACK into the main repositories has been the most surprising and rewarding advancement to date. Surprising because it had not already been accomplished and rewarding because many applications were then able to be built against JACK to harness that functionality.

 ***AG:******What do you see the Ubuntu Studio project becoming over the next 3 to 5 years? How can those goals be realized?***

 **SL:** I would like to see Ubuntu Studio accomplish at least two things in the next 3 to 5 year; develop an active and supporting community around it and to identify and explore the possibility of cultivating additional user bases.

 KDE has a rich and vibrant community, something similar is what I would like Ubuntu Studio to develop. This would be characterised by significant and frequent user suggestions and feedback, user contributions of art and music to be include in the releases and web site, and user testing of ISO images and bug fixes. Already users routinely report bugs, for which I am grateful.

 There has also been discussion about broadening Ubuntu Studio into universities and perhaps semi-professional / indie bands. But these discussions are embryonic at best and we need to improve the development team before we should consider this again, especially given the fact that these additional user bases would probably be inexperience with Linux or Ubuntu.

 To realize these goals the development team needs more active members. I mentioned it before, but it worth mentioning again, *anyone* can contribute, you do not need to be a developer to help Ubuntu Studio! And hopefully we can improve community activity which will be required as well.

 ***AG: ******Where can people go to download Ubuntu Studio? Where can they find support documentation? What resources do you have for people to contact the team?***

 **SL:** Probably the most comprehensive and current place for Ubuntu Studio ISO images is: [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

 Support documentation is generally divided into two categories; [using Ubuntu Studio]("https://help.ubuntu.com/community/UbuntuStudio") and [developing / contributing to Ubuntu Studio]("https://wiki.ubuntu.com/UbuntuStudio").

  The team can be contacted by [mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel") or on the IRC channel #ubuntustudio-devel on freenode.net.

 ***AG:******Scott is there anything else you would like to tell readers about Ubuntu Studio that I haven’t asked you about?***

 **SL:** No, I think all items I can think of have been covered already.

 Thank you for this interview and the chance to bring Ubuntu Studio into the collective consciousness.

 Originally posted [here]("http://www.ubuntu-user.com/Online/Blogs/Amber-Graner-You-in-Ubuntu/Talking-about-Ubuntu-Studio-with-Scott-Lavender-Project-Lead-for-Ubuntu-Studio") by Amber Graner on August 11, 2010

 

[More...](http://fridge.ubuntu.com/node/2099)

---

