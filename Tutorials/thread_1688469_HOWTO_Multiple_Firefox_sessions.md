---
title: "HOWTO: Multiple Firefox sessions"
date: 2011-02-15
forum: Tutorials
---

### Post by miki4242 on 2011-02-15
This HOWTO may be useful for people who want to:

[LIST]
[*]Browse the same website in different Firefox windows, each logged in as a different user
[*]Open a private browsing session while keeping other Firefox windows open
[*]Work with Google services while logged in with multiple Google accounts
[/LIST]
My personal motivation for writing this HOWTO:

When working with GMail, Google Docs etcetera, I found it very annoying that new Firefox windows I opened would open with the Google start page (which I've set as my default) _and_ logged in with my Google account. When I would sign off in any window showing a Google page, all other windows showing Google pages would sign off or close as well.
Call me paranoid, but I simply don't like Google watching over my shoulder when searching for stuff or clicking links when I happen to be working with my GMail or Google documents in some other browser window.

After searching around for an explanation for this, I've found out the following:

[LIST]
[*]When you open a new Firefox window, either by choosing 'File'/'New Window' or clicking on a Firefox icon, this doesn't actually start a new Firefox session but re-uses the current one instead.
[*]Most importantly, this means that any website logins that were active before opening the new window are still active in the new window.
[*]Logging out of a website in the new window will most likely log you out of that site in other open windows, and in some cases will cause very strange behaviour if the site in question has certain design flaws.
[/LIST]
This is the way I've managed to fix this:

First, create a new Firefox profile by starting Firefox's Profile Manager. This profile will be used for browsing a website for which you need to log in (GMail in this example).

[LIST=1]
[*]At the desktop, press [Alt]-[F2] (hold down the Alt key while pressing the F2 key). This will open a dialog titled "Run Application"
[*]In the text box, enter: ```
firefox -no-remote -P
``` . This will start Firefox's Profile Manager
[*]In the window which pops up, click on "Create Profile"
[*]The Create Profile Wizard opens
[*]Click "Next" to continue
[*]In the text box under "Enter Profile Name", enter a meaningful name for the profile. Don't use the name 'default'! In my case, I entered my GMail email address.
[*]Click "Finish" to create the new profile
[*]Click "Exit" to close the Profile Manager
[/LIST]
Voilà, the new profile is now created. To use it, create a special Firefox launcher icon which can be placed on the desktop or in a panel.
To do this:

[LIST=1]
[*]Open the Applications menu, choose "Internet" submenu
[*]Right-click on the "Firefox webbrowser" menu entry
[*]In the pop-up menu which opens now, click the option where you wish the new launcher to be placed, either on the panel or on the desktop.
[/LIST]
Now the new launcher must be set up to use the Firefox profile created earlier. To do this:

[LIST=1]
[*]Right-click on the newly added Firefox icon
[*]Select "Properties"
[*]In the window which opens, click in the "Name" text box
[*]Change the text there to something which is easy to remember. I simply added my GMail email address at the end.
[*]Next, click either the "Command line" (if it is a panel launcher) or "Command" (if it is a desktop launcher) text box.
[*]Make the text in the box look like this: ```
firefox -no-remote -P "<your profile name>" %u
``` . (replace <your-profile-name> with the name you chose for the Firefox profile you created. Don't remove the quotes!)
[*][IMPORTANT] I needed to click inside one of the other text boxes (don't change anything!) to make the change 'stick'. This could be a bug of some kind.
[*]Finally, click "Close"
[/LIST]
Finished! Now you have a new Firefox launcher to start a new session.
Note that the new session is completely 'pristine': you will need to log in to the website you wish to use, set your home page, install all your favorite plugins, add bookmarks, etc.
You can repeat the entire procedure and create as many new profiles and launchers as you like, one for each session type.

More information on Firefox command-line options can be found via [this link]("https://developer.mozilla.org/en/Command_Line_Options").

I hope that this HOWTO is useful, please add any comments or questions you may have, and I will try to answer them as best as I can.

---

### Post by Nublet on 2011-02-17
thanks! i have a separate account for my bank accounts, and it always annoyed me how i couldn't access it while browsing. it should save me a lot of hassle.

---

### Post by carbon512 on 2011-12-14
Bumping this old thread to ask - how can I make a launcher for this second firefox session/profile in Unity? So I don't have to use command line to launch it every time?    

And, once I do this, how can I differentiate the two lauchers? (Used to do this on a Mac with two different icons for the FF aliases in the dock) Can't figure this out... thanks!       

(I feel the same way about being logged in to google, having to accept google cookies, etc. Paranoid? Maybe. Skeptical? Definitely.)

---

