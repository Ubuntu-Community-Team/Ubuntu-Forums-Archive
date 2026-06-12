---
title: "loading e-Sword utility programs like TheWORDpad"
date: 2008-10-15
forum: Ubuntu Christian Edition
---

### Post by rojen on 2008-10-15
Hi all!

I worked with Unix for yrs, then was moved to a windows position and stayed there for yrs.  I have been retired for a few and really wanted to go back to unix.  The last thing really holding me back was e-Sword.  I have used it since it came out and it is a wonderful help in my life and ministry.

So with that hurdle dying, I am moving to linux.  But, I am having a challenge with the e-Sword utilities which I need for some update editing I am doing to jet db modules.  Nothing worth releasing yet, but I enjoy the work.  

What I am working on is a Bible module currently so a good tool for that is needed.

What I tried to install is TheWORDpad v2.  It is having a problem and gives me an error msg at the command line saying it needs riched20.dll by the riched32.dll.  Then a pop-up comes saying to load mdac 2.1 or later.

I went online and looked at the mdac stuff.  The one available at microsoft no longer have any jet db stuff in them.  So I reapplied the rules for e-Sword installs concerning dll's to no effect.  I re-installed in a container and not in a container with the same challenge.

Has anyone gotten the utilities to run well?  Any tips available?

I also looked at mdbtools which is in native linux.  But never I did not attempt it yet.  It looks maybe less than simple and is in beta at present.

I appreciate any help,

Ron Nieuwsma

---

### Post by david_kt on 2008-10-15
> **rojen said:**
> 
What I am working on is a Bible module currently so a good tool for that is needed.

What I tried to install is TheWORDpad v2.  It is having a problem and gives me an error msg at the command line saying it needs riched20.dll by the riched32.dll.  Then a pop-up comes saying to load mdac 2.1 or later.

I went online and looked at the mdac stuff.  The one available at microsoft no longer have any jet db stuff in them.  So I reapplied the rules for e-Sword installs concerning dll's to no effect.  I re-installed in a container and not in a container with the same challenge.

Has anyone gotten the utilities to run well?  Any tips available?


I just tried TheWORDpad v2 using wine-1.0, there is no riched20 or riched32 problem. Please use a clean wine.

I get mdac2.1 error, but it is very easy to fix. Just install mdac 2.5, it could run properly.

Go here:

[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Open text editor and copy and paste the above text, and save it as winetricks.

Make the saved file executable (right click, properties, permissions, tick execute).

Run winetricks and choose mdac25.

After that, you should be able to run TheWORDPad v2.

DK

---

### Post by rojen on 2008-10-15
I praise God, this was a blessing.  I thank you His servant DK.  Your notes were perfect and I am back in business!

ron

---

### Post by rojen on 2008-10-15
The machine I am using is an old laptop with Linux shoehorned in.  Unfortunately it seems in sufficient for editing large db files from jet.  I get a message warning me, then the whole thing errors when I try to access the tables.

Any suggestions?  

Let me give a little details of this project.  I am rewriting the Bible just for the sake of learning and studying it.  This is not to make a new Bible, but to help sew it into my heart.  I read of other saints doing this long ago, and thought the idea had great merit.

I want to use e-sword, because i will use the bible I rewrote and because I can easily ck for errors with the compare process.

Thanks,
ron

---

### Post by david_kt on 2008-10-15
> **rojen said:**
> The machine I am using is an old laptop with Linux shoehorned in.  Unfortunately it seems in sufficient for editing large db files from jet.  I get a message warning me, then the whole thing errors when I try to access the tables.

Any suggestions?  

I have not try to open db files as it require password to open it. So, I am not sure whether the error was due to old laptop or due to wine.

Could you let me know exactly the message warning?

> **rojen said:**
> 
Let me give a little details of this project.  I am rewriting the Bible just for the sake of learning and studying it.  This is not to make a new Bible, but to help sew it into my heart.  I read of other saints doing this long ago, and thought the idea had great merit.

I want to use e-sword, because i will use the bible I rewrote and because I can easily ck for errors with the compare process.

Thanks,
ron

It is very good effort I think. The main point (in my opinion) is when we deeply concentrate on good things (in this case bible), we enter the so called "meditative state" and it could bring our spirit to a higher level.

DK

---

### Post by rojen on 2008-10-16
Thanks again David.  I am thankful to God for all the help I get.

The error msg is fairly verbose:

It starts the Bible module file you wish to open has a file size of 18,255,872 bytes.

Opening larger e-Sword modules files with TheWORDpad might possily cause the program to crash.  This is partially due to limitations within the windows dll that TheWORDpad uses for its data grid display, but it is also due to the fact that opening entire tables in large database files requires quite a bit of computer memory and processing power.  

(two more paragraphs of this), then continue yes, no, cancel.

I click yes and it *opens* the Bible with two tables showing.  Bible and details.  I click on Bible and it goes away for a while and then gives a popup saying "can not initialize data bindings."  I enabled logging and got the following:
TWordPad : 10/16/2008 18:24:20 : CMainFrame::OnClose() called
TWordPad : 10/16/2008 18:24:20 : CMainFrame::WriteWindowPlacement() called
TWordPad : 10/16/2008 18:24:20 : CMainFrame::WriteWindowPlacement() szBuffer = 0,1,0,0,0,0,0,0,768,576
TWordPad : 10/16/2008 18:24:20 : CMainFrame::OnShowWindow() called
TWordPad : 10/16/2008 18:24:20 : CDataGridView::OnActivateView() called
TWordPad : 10/16/2008 18:24:20 : CMainFrame::OnActivate() called
TWordPad : 10/16/2008 18:24:20 : CMainFrame::OnActivateApp() called
TWordPad : 10/16/2008 18:24:21 : CDataGridView::OnActivateView() called
TWordPad : 10/16/2008 18:24:21 : CMSDataGridApp::ExitInstance() called

I am not tied to this editor any editor that lets me edit verses simply and easily will do.  This one has a lot of nice options like spelling dictionary and stuff so it was my first choice.

In my old days I would have attempted an ODBC connection using a mysql database editor on the front end.  But I can not remember much beyond it existing these days and setting those up can be simple or quite tricky, kinda like knowing to use winetricks in setting this up, lol.

Thanks,
ron
PS I haven't updated my profile yet but we are both in Asia.  I am in the Philippines.

---

