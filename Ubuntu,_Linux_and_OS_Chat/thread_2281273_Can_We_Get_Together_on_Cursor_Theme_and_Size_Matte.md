---
title: "Can We Get Together on Cursor Theme and Size Matters Here?"
date: 2015-06-05
forum: Ubuntu, Linux and OS Chat
---

### Post by oldefoxx on 2015-06-05
I'm serious.   Depending on what I use to track down posts on the subject, I find different suggestions and possible solutions.  But invarably, I will also see that not all the solutions work well together, and at some point I will see a different cursor show up at some pointas I move it about the screen.  It will sometimes be a different style cursor (called a theme), but more often it will be in a different size.

In 14.04, I would have to say that there are just too many things that conflict over each other in this matter.  Too many places and too many ways where a theme has to be named or a cursor size setting is called for.  So let's get it all together here and get it so you are dealing with just one theme and one mouse size across the board.

Okay, here are a few things I noted so far from my own experience.  And trust me, I am not exaggerating when I say I am no expert in this.  I;m just asking those that really know a bit about the matter to help in this search for the truth, the ehole truth, and nothing but the truth.  I hear that in court scenes on tv and in the movies a lot, so why not include it here?

Problem #1:  What are the cursor size settings and what should the scaling factor for each be?  I've run into 24 (small), 32 (medium), 48 (large), and 64 (huge) a lot.   But I have found mention of another size, that being 36, but that possibly was just a posting error.  Maybe they really meant 32.  What I also found was mention that cursor theme size is always a multiple of 8, which would rule out use of 36.

We have some cursor themes that include one of those terms (small or regular, medium, large, or huge) in the theme name, which makes it easier when dealing with one of them.  But there are many cursor themes that can't be picked out this way, and a number of those are scaleable.  So you get into cursor-scaling-factor for those, a figure that appears several places, and I would rhink you would want these to all match up with each other.  But apparently they don't.

What should the scaling factor be?  Actually, there are a number of things that can be scaled up and down in size, such as text or headers.  This gives us our zoom capabilities and the means of mixing different size text into documents and having them display properly.  So far, my searches have turned up these sizes for the cursor-scaling-factor:
     1.  For 24, use 1.
     2.  For 32, use 1.35 (one place said use 1.25.  Would this be right?)
     3.  For 36?  Use 1.5?
     4.  For 48, use 2
     5.  For 64, use 2.65 (3 is the very top).

What I'm thinking is, that if 24 is small, and we are dealing with multiples of 8 here,  That 48 is twice 24, so it makes sense that it should be 2.  But from 24 to 32, that is a count of 8, and from 32 to 48 is a count of 16, so  32 is 1/3rd the way from 24 to 48, and a scaling factor of 1.3333333... is indicated, but we can round up to 1.35 if that is generally accepted.  A size of 36 would be half the distance from 24 to 48, and would correspond to a sizing factor of 1.5.   But in termes of fized-sized fonts, I don't think 36 matches up, so it must scale down to 32.  I would think.

The huge size, 64, is as much as 25 and 48 added together, and if the scaling for 24 is 1, and the scaling for 48 is 2, then the scaling all the way up to 3 represents 96, which is unlikely.  The difference between 96 and 48 is 48.  Natural, since its just double.  The difference between 48 and 64 is 24, and 24 is half of 48.  So by adding .5 (1/2) to our 2.0 (for 48), and we see that 2.5 seems right.  But what I've found is that some are chosing to make this 2.65, no reason given.

I have followed instructions provided by others on this forum with reasonable results.  But it's not altogether in one place, and with your help, we can make it simpler for everybody, anf hopefilly get it together in just one post that does it all.  I don't expect to be the originator of that post.  In fact, to make it simpler all the way around, let's make the first person to answer this post keep editing it to incorporate any suggestions that come out in the posts that follow.  I mean I had a good post made on a separate thread that I have gone back to numerous times, and had to find the thread (title was no help), and get all the way to Post #20 (which took a bit too much time).  So Poster #2, be a volunteer and do a good job of it.  The rest of you, wait for post #2 and put forth your best ideas of what coding should go in there.

As you can see, I say a bit too much as I go along, so I leave it to someone else to take on that role.

Oh, parting shots.  And let's make them some good ones:

(1)  Cursor Themes are generally stored in /usr/share/icons.
Not all the folders in there are cursor themes.  But for the ones that are, you need to ensure there is already a file in it named cursor.theme, and if not, just copy one out of the DMZ-White folder and use a text editor like gedit or nano to change the 'Inherits=' line to reflect the exact same name as given to the cursor theme folder that it is going into. 

You can find, download, and add more cursor themes from gnome-look.org. You will be able to extract the contents of compressed files easily  (Just double-click them with the left mouse button and an Archive Manager will open it for you), and good temporary storage is just extract them to your Desktop.They aren't going to stay there, but you have a decent view of them while you are working eith them.

Gettting them into /usr/share/icons is more difficult, but not much.  Your user identity does not have permissions for getting into /usr/share/icons, but you can go to terminal mode (use Terminal, UXTerm or XTerm) and that gives you command line mode access to the system using a provided shell.  The default shell is named 'bash', and it seems everybody pretty much uses it now, so it's just understood that bash will carry out the commands you enter, until you either type 'exit' or close the terminal window.  A 'shell' is just a command line interpreter that recognizes some entries made as things for it to do for the user, or if it dose not see what is entered as a valid command for it to follow, it tries to find a file by that name that is flagged as executable and call it for you.

first command you can do is:
dir Desktop

Some prefer the older 'ls' command instead of 'dir',  but either one will do.  Actually, after a reinstall of Ubuntu, the bash shell could not resove either 'dir' or 'ls', but apt-get told me that I had several possible candidate sources.  The obcious choice was 'coreutils', so I asked apt-get to install it for me, only to learn it was already installed.  But after that, the commands worked again. Now let's continue.

This will list the contents of your Desktop folder, and this list will include all the cursor theme files you extracted to it.  Incidently, if you don't know where your downloaded files went, by default they are in your Downloads folder.  Because you can change your current relative position with use of a 'cd' command, you are often advised to preceed your own folder rederences off your Home Folder with a tilde '~' character, which always relates to your home folder regardless of which current directory you are in.   You see a path starting with '~', that is with regards to /home/[username], with [username] being your username.  You see a path starting with '/', that is from the root reference to the start of all its file structure.  You should read that as everything under /home belongs to the users, and everything else belongs to root and is merely shared among the users.

The 'cd' is short for 'current directory', and directory is just a Window's way of speaking of a folder.  So 'dir Desktop' becomes 'dir ~/Desktop', and 'dir Downloads' becomes 'dir ~/Downloads'.  You see the Present Working Directory at the start of each command line, and you have a 'pwd' command that also tells you where ypu are positioned in the file structure at this moment.

What you want displayed on the terminal screen is the name of the cursor theme you want to try to use.  Now if you have a lot of themes, and/or they have long names, you may not still see the name you you want, due to it just scrolling off the screen by the time the list is complete. You can maximize your terminal sindow and use the up-arrow key to repeat the same command and get a repeated list, which should incease the number of names displayed per line, or you can drastically reduce the listing shown if you enter only a part of the cursor theme name you want, plus a trailing asterick '*', and even make use of a leading asterick '*' if the part you want is within, not the leading part of the name,  Here are some examples:

dir ~/Desktop/DMZ*
dir ~/Desktop/Comix*
dir ~/Desktop/*Large*
dir ~/Desktop/*Medium*

The asterick is referred to as being a 'wildcard', and can be real handy.  For instance, unlike Windows, Linux is case-sensitive, meaning 'large' is not the same as 'Large' or "LARGE'.  To deal with just the first letter of a word might be capitalized (or not), you can limit your search to the letters that are expected to be small, as in these two examples:

dir ~/Desktop/*arge*
dir ~/Desktop/*edium*

The use of wildcards can be applied to other commands at this point.  If the results of your last 'dir' command includes,AND IS LIMITED tO, cursor themes that you want to move to /usr/share/icons.  you can use your up-arrow key to bring back that same command and make some changes to it.  You use the left- and right-arrow keys to nove to where you want in the command line (the line where the terminal lets you type), and you replace 'dir' with /sudo mv', then you go back to the right end of the line and add ' /usr/share/icons/'.  When you press the Enter key, those identified folders will be moved to the /usr/share/icons folder.  They won't be on your desktop anymore.

if you want to delete the compressed file they came in, you can do this, using the same wildcard trick:  'rm ~/Downloads/*[whatever]*.  By "whatever", I just mean that it can be less risky to just use the up-arrow and bring back the last command again and replace 'mv ~/Desktop' with 'rm ~/Downloads'. , but you also have to take off the added ' /usr/share/icons/'.

Let's reorganise and do it in this sequence:
dir ~/Desktop/*edium*

That's what I want.  So delete the compressed file first.  Replace 'dir ~/Desktop' with 'rm /Downloads' so that we have this:
rm ~/Downloads/*edium*'.

So let's put these Desktop files into /usr/share/icons by replacing 'rm ~/Downloads' with 'sudo mv /Desktop' and adding ' /usr/share/icons/'  to the end of the line like so:
sudo mv ~/Desktop/*edium* /usr/share/icons/

Now you can also just use the GUI File Manager (named 'nautilus') to move and delete files, but to work with /usr/share/icons, we have to have root priveleges.  That is what 'sudo' gives us, just for that one command.  But to act like root and use the GUI (Grapical User Interface where you can see things happen visually, we have to engage nautilus with super user powers.  You can do that this way.  Open a terminal window (unless you already have one open) and enter this on the command line:  I tried this method, but nautilus generated an error report, so I just used ther terminal command line method outlined here. If you use Dash (I don't), I have found 3 wasy to fet into your file sustem.  (1) The 2nd icon on the left side screen (in what I think of as a totem pole) is for your File Manager.  It's quick and easy to get to.  (2) In Dash, you can type 'files'.  This gets you to the same place.  (3) In Dash, you can type 'home'.  This gives you access to both hour Home folder and shows '/' where you can get to root.  But do anything beyond your own Home folder and subfolders, you have to have super user capabilitues.  Dash does not give that to you up front.  But open a terminal and type 'sudo dash' in it, and it drops you right into super user mode, but without displaying the present working directory as part of the command line.  I find that interesting.
gksudo nautilus

or you can endure a few warnings and enter this instead:
sudo nautilus

And after entering your user password, you should have the File Manager come up on the screen for you.  Now you can get to /usr or any folder by going to computer, which for me with the classical gnome environment, is under Places.  I'll try to remember to log back in under Dash (the new look and feel of gnome) and see how you get around the file system with that.   It's not that was apparent the few times I logged into Dash, and the only reason I had for doing it was to relate as closely as I could to what someone had written in a post online.  

If using Dash, you have three ways that I know of to get to a file manager easily.  The first just means using the Files icon right below the Dash icon on ledt side of the screen (what looks like a totem pole to me).  (2)  Under Dash, enter 'files'.  Gets you to the same place.  (3) In Dash, enter 'home'  Gets you to your Home folder and also shows '/' for getting to the root folder.

Warning!  Doing copy ('cp'), move ('mv') or delete/remove ('rm') with wildcards (*) can be risky business because if ANYTHING you did not plan to include also matches up, that action will happen to it as well.  That is why you need to check out what DOES match up first with a 'dir' or 'ls' command, and check shet shows up carefully.  You blow this, you may lose something or misplace it, and straightening that out can be a nightmare, because you have to figure out what you did wrong and what steps to take to undo it.

Root or super user priveleges mean some nasty consequences if you make a mistake.  So what I usually do is hunt for a post somewhere that spells out the steps in detail and use the copy-and-paste method to get the command line entry as right as possible.  Copy from most sources is highlight with the mouse or cursor keys first.  You hold down the shift key, and the highlight follows where you go on the screen.  Then you use the Ctrl+C keys together to copy that to the clipboard (an area of memory that is used for this one thing).

When you paste into the terminal, it will always be at the point where the flashing cursor is, which is somewhere on the command line.  The paste is actually an insert, meaning anything after that point just gets pushed over to the right to make room for the inserted text.  Copied text can include the Enter key on the end of lines, so back up if necessary to avoid immediate execution of the line up to and including what you pasdted in.  Immediate execution is definately not wanted if you have to modify the line before doing anything with it.

To remove what you don't want from the command line, you use either the Backspace key or the Del key.  The Backspace key removes the character just before where the cursor is.  The Del key removes the character under the cursor.  The visual effect is, that with Backspace, you get rid of what;s left of the cursor one character at a time, and with Del, you remove what is right of the cursor one character at a time.  The mouse is only used for copying something from the terminal screen by highlighting it (only the moise works for this, not the cursor keys), then pressing Ctrl+Shft+C together (the letter key is always pushed last).  If you immediately follow this with Ctrl+Shft+V, what was highlighted will insert into the command line exactly where the cursor sits.  The character under the cursor is shoved to the right to make room for the insert.

It's going to seem too obvious and too fundamental to explain any ot this to a lot of readers of this post, but please recognize that not everyone is up to speed with computers as you are, and for many, this may be their first go at using the terminal and getting into command line mode.  I'm just trying to play my part here, and do what I can to help.  But it iis also why I am not the best person for laying out a procedure or explaining a process of getting a cursor to look right on the screen.  There are others who are far better suited to do that.

---

### Post by cariboo on 2015-06-05
Not really a support request. Moved

---

### Post by oldefoxx on 2015-06-05
Well. that take care of my idea of the 2nd poster pulling all the data together as this thread grows.  And I'm not the best choice by far. so that blows the 3rd post position as well.   So somebody please step up and take the task on, and we will correct the numbers later to point to whatever post position you find yourself in.  Just so we get it together.  It could be a real help to ourselves and others.

As a matter of curiosity, I got back into the classic gnome mode, brought up a terminal window and entered 'sudo dash'.  As before, I had to enter my password andd I got the super user prompt of '#'/  I typed 'nautilus', and got quite a response/  mautilus came up okay, but there were sharing issues indicated.  Here is a screenshot of what I got back.  Seems like in this mode, samba has to be installed as well.

This is not as good a way to work as just using sudo in a terminal window.  The editing features for the command line aren't really there.  Still, I suspect it has its purpose in the scheme of things.

---

### Post by CantankRus on 2015-06-06
> **oldefoxx said:**
> 

As a matter of curiosity, I got back into the classic gnome mode, brought up a terminal window and entered 'sudo dash'.  As before, I had to enter my password andd I got the super user prompt of '#'/  I typed 'nautilus', and got quite a response/  mautilus came up okay, but there were sharing issues indicated.  Here is a screenshot of what I got back.  Seems like in this mode, samba has to be installed as well.

This is not as good a way to work as just using sudo in a terminal window.  The editing features for the command line aren't really there.  Still, I suspect it has its purpose in the scheme of things.

The errors are probably related to the fact you should use **gksudo** and not **sudo** for graphical applications.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by oldefoxx on 2015-06-11
How do I make it so the cursor is always on top?  Several applications can't be managed properly because the mouse disappears when I move over them.  In my mind, the cursor should always be on top.  How do I make this happen?

---

### Post by CantankRus on 2015-06-11
Which applications?

---

### Post by oldefoxx on 2015-06-12
There are several, but naming them was not something I was prepared to do.  Gowever, it just happened to me with SlimBoat.  I lost the ability to see the cursor in parts of the toolbar, in trying to select certain tabs, or to use thcursor visably inside an opened page, which was to a commercial site where I was trying to price a new or refurbished laptop.  Rhis one is fine, but I need more than 4GB RAM, and I still need a 17.3" screen.   

SlimBoat is proving to be a handy little browser, but I'm pushing it hard enough to make it use the swap drive, a situation that more RAM should solve.  Trouble there is that search engines won't let you search for double quotes, so I can'r search on 17" or 17.3", meaning inches.  We had this proglem solved back in the 1960's by accepting single quotes as well, so that you just surround a double quote with a pair of single quotes, like this: '"'.  In HTML/XML, you can also insert a 2-character hex value for a character after a percent key, like %03 for an Enter key.

With search engines, you are also hindered by matches anywhere in a given file, like in a web page.  If that web page is listing a number of items for sale, there is no way to restrict the search to just a portion of the document.  I've proposed they include some additional parameters like this:

c<300:   max distance between characters/terms that match is specified, in this case, 300.
l<20:             --  max number of cr, lf, or crlf pairs in the matched area is defined, here set as no more than 20 lines.
*                   --  consecutive order of terms required
John * doe      --  anything in between, possibly a middle initial or name, but maybe a lot more
john*doe        --  only a space or punctuatuon mark can separarte the two terms
*john             --  can be preceeded by anything, not restricted to space or punctuation mark of some sort
john*             --  can be followed by anything, not restricted to space or punctuation mark of some sort
john               --  must be preceeded and followed by a space or punctuation mark such as cr, lf, or tab.
?john              --  serves to wildcard one position before term.  You can have multiple like  ??????????
john?              --  serves to wildcard one position after term.
john & doe       --  the terms must be must be consecutive,  term1 before term2
john&doe         --  the terms must be within one term of each other
john&&doe       --  the terms must be within two terms of each other (allows for MI or middle name) 
" "                   --  what's between is case sensitive ("John"&&"Doe" won't match on "Paul Johnson says he doesn't...")
' '                    --  what's between is case insensitive.

Seems to be an odd case to be going over this, but search engines are driving me up a wall right now.  I can't
find a one that lets you search for the double quote character.  And suddenly having a cursor that won't show up is not helping.

---

