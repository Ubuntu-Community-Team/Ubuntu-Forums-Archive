---
title: "Linux DaisyPlayer project"
date: 2006-05-02
forum: The Cafe
---

### Post by daisyplayer on 2006-05-02
Hi!


**Who might this interest?**

* People who use or are involved with DAISY digital talking books.
* Linux developers and enthusiasts who would like to test or contribute to a new project.

**What is a DAISY digital talking book?**

DAISY is a digital talking book format. Simply put, it's an audio book with synchronized text, and helps users who have problems seeing or reading traditional printed media. It also supports navigation methods which traditional audio books lacks.


**Why this project?**

We are four students at Gjøvik University College in Norway (who are all new to software developing on the Linux platform), working on a project for our bachelor assignment. The project are currently in its final stage, and we would like to advertise our project.

Our project goal is to start a software project and to create a program that handles playback of audio books in the "DAISY Digital Talking Book" format. This has been requested by the Skolelinux organization. Many schools today use DAISY books. By offering one or more Linux players for these books, initiatives like Skolelinux / DebianEdu will hopefully be better suited to meet the needs of these schools.

The DaisyPlayer Project is an Open Source Linux project for playing Digital Talking Books, licensed under the GNU General Public License.


**A brief technical description:**

To this point, we have made a shared library - a "DAISY engine" that is capable of parsing and playing DAISY audio books. Together with two different front ends (one console front end (daisyconsole) and one GUI front end (daisygui)) you can play your DAISY DTBs in the Daisy 2.02 and ANSI/NISO Z.39.86-2005 standards.

We have put most of our effort into making an engine library, and created a API for it. The two front ends we have created are meant to be examples demonstrating how to use it. The engine and the console front end is written in ANSI C 89, and the GUI front end is written in C++ using Trolltech's Qt3 Designer. We have also put a lot of effort into commenting our source code, so that it would be easy and understandable for others to contribute to the project.


**Why this announcement?**

Our hope is that someone will find our project useful or interesting. And that someone will help the project by testing the software, contributing to the project and help us create a program that will make Linux an even better alternative to people who need DAISY books.


**Can I Help?**

If you use or are involved with DAISY books, you can test our software and give us some feedback.
If you are a Linux programmer, you can download and browse the libdaisy source code and see if you can contribute, either by improving on the source code or assist in debugging.
If you are experienced with threads programming, you can probably help out locating some bugs and improving the libraries stability.
If you area a GUI expert, you can take a look at the libdaisy API. You can improve on our example front ends or create a new front end that is even better.


**Where can I learn more?**

You can head over to our website [http://developer.skolelinux.no/info/studentgrupper/2006-hig-daisyplayer/](http://developer.skolelinux.no/info/studentgrupper/2006-hig-daisyplayer/) or ask google for "daisyplayer".
And, of course, you can mail one of the developers. Our goal is to make this project as good as we can, so we will appreciate any questions and feedback.

---

### Post by daisyplayer on 2006-05-03
Our website is now updated with some screenshots and a FAQ.

----
[http://developer.skolelinux.no/info/studentgrupper/2006-hig-daisyplayer/](http://developer.skolelinux.no/info/studentgrupper/2006-hig-daisyplayer/)

---

