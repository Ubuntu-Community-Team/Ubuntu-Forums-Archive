---
title: "Better translation QA"
date: 2011-01-27
forum: Ubuntu Translations
---

### Post by YaronSh on 2011-01-27
[CENTER][SIZE="6"]_Typo reporting function_[/SIZE][/CENTER]

**Motivation:**

[INDENT]In Ubuntu the "Translate this Application" menu item under Help has become completely useless recently and I think we should consider an alternative while utilising gnome-screenshot and apport.

Our goal is to enable an easy and quick way to report typos in apps, in the attached picture I described 5 simple steps to do so (this can also help detect visual glitches in apps or RTL problem, just a thought).

Possible cons:
The app in undetectable or the user decides to report a typo in a website while thinking this is a problem with the app (although highly plausible).
There will be too many bug reports to handle, Launchpad changes are required for this to work.[/INDENT]


**1st step:**

[INDENT]After spotting the typo the users can just click on Help -> Report a broken translation.
This action will launch a series of actions starting with gnome-screenshot -a (that will capture a specific area of the screen) the next actions should somehow prepare the file and add save it to a temp folder (/tmp in our case, gnome-screenshot).[/INDENT]


**2nd step:**

[INDENT]The user will be presented with a crosshair so he can select the desired area, (small floating message on top to bottom of the screen is optional, we have to make sure that the screenshot tool will not capture the message &#9786;)[/INDENT]


**3rd step:**

[INDENT]The user will have an option to state exactly what seems wrong in his opinion and offer a correction. (in 2 distinct text boxes, 3rd box for comments is optional and I didn't add that in the mockup)
Another option we can offer (does not appear in the mockup) is to add a small window on top that will show the user a thumbnail of the captured area.[/INDENT]


**4th step:**

[INDENT]The following screen associates the typo report to the user using 3 options:
The user will have the ability to log into his Launchpad account.
The user does not have a Launchpad account and he decides this is the right time to sign up.
The user have no interest in a Launchpad account, but he wishes to be informed of any further progress.
The first option will show a username/password boxes for logging in.

The second option will open the default browser with a registration pag, the two option are: sending the report at this step and not publishing it until the user sign up, if the user does not sign up the report is deleted within 24 hrs, the second option is adding a message at the end of the registration progress, at this point the user will dismiss the browser window and go back to the report window where he can sign in and continue.

The third option will show a text box for entering an email address and a captcha (turing test) and a checkbox so the user will have the option to subscribe, we should consider whether its safe to let the users submit reports anonymously.

This step involves the usage of apport (which I'm not familiar with), apport will collect the needed info about the system language etc. including the app name and version and will make sure that the report is good enough, apport also has the option of adding files to Lunchpad bug reports, this makes reporting a little more automatic (future thoughts: make this a GNOME native function using bug-buddy).[/INDENT]


**5th step:**

[INDENT]The final screen, which shows a short greeting (your bug report has been submitted or otherwise not submitted in case there was an error and maybe even tells you what went wrong).
The link to the bug in the middle.
And finally a short message that thanks the user for taking the time to make the open source better.[/INDENT]

Reported as brainstorm [idea 27054]("http://brainstorm.ubuntu.com/idea/27054/")

Kind regards,
Yaron Shahrabani.

---

### Post by ofir_k on 2011-02-06
First of all, I would like to say that this idea can really contribute to the translation process. The translation of an application requires from the translator to find the context of the string she/he is translating.
By giving the user the option to report a typing error with a screenshot of the typo attached to the bug report, the translators can easily fix the typo, and with according to the string context.

Just for the convenience of those who want to see the correct thumbnail, I attached all the steps in a nice and easy way:

---

