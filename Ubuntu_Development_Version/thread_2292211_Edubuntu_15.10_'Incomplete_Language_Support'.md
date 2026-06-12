---
title: "Edubuntu 15.10 'Incomplete Language Support'"
date: 2015-08-26
forum: Ubuntu Development Version
---

### Post by genesoo77072 on 2015-08-26
Two questions about this exception.

First, When this exception comes up shortly after first boot after you successfully perform the Run This Option actions, the original exception reporting window remains giving the user the impression that the exception remains.
Question: Should Successful Completion of the "Run This Action" kill the Exception Reporting Window?

Second, it seems that during the installation process, there is a lack of dealing with user's desired language support.
Somewhere when it asks for the Supported Keyboards, your languages should be identified and this action should be carried out.
Question: Should the actions to create language support be incorporated into the installation process be handled at install time rather than as a post-install exception?

I would love for the second issue to be addressed to reduce installation interactions however if that cannot be accomplished then the first issue is relevant for removing ambiguity for dealing with whether the exception still exists after complying with the requested action.

Whomever answers this, I am a Noob reporting these issues so please include recommendations on how to make an official report(bug/design change) if this is not the proper forum.
I am thinking the #1 may fit into the Bug category and #2 is a design change.

---

### Post by dino99 on 2015-08-26
hi,
is that installation made with the 'daily' iso, or with the mini.iso ?
usually when the installer try to identify your keyboard, it ask you to hit some keys, then return a keyboard proposition you need to validate, then the required language is selected. You still can change/tweak (when the installation has ended, and rebooted) the language via 'System Settings' both for regional & system wide.

if you need to report bug(s), then open a terminal, and run:
> ubuntu-bug <packagename> this will do the required stuff and send the report on your launchpad account (which you need to create first)

---

### Post by grahammechanical on 2015-08-26
It has been some time since I installed Edubuntu but I am confident that Edubuntu uses the same installer as Ubuntu and the other flavours of Ubuntu. At the very beginning of the install process we can set the default language. It is most likely the first screen we see after clicking Try Ubuntu or Install Ubuntu.

[URL="https://help.ubuntu.com/community/GraphicalInstall"]https://help.ubuntu.com/community/GraphicalInstall

[/URL]And there is another way we can set the language. As the live session loads we see a screen with an icon of a human and an icon of a keyboard. Press Enter and a screen will appear where we can select a language. The default is English. Select the language and press Enter and we get an underlying screen where we can select either Try Ubuntu or Install Ubuntu and some other options.

After we have installed Ubuntu/Edubuntu we can add other language keyboard layouts. I have done that but I do not need the spell checker for this second language so I have not added full language support for the new language keyboard layout. Therefore, when I open System Settings>Language support I am advised of "incomplete language support". I do not see that as a problem.

Complete language support is installed during the installation of Ubuntu for the chosen default language. It is only when we want to add other languages that we have to add those languages after Ubuntu is installed and it is a 2 stage process. 1) Install the keyboard layout. 2) Install dictionaries and spell checker. Or we will be reminded that language support of that language is incomplete but only when we open System Settings>Language support. 

What you are seeing is not a bug or a bad design. It is the way Ubuntu does things and it is designed that way to keep the installation process simple by having minimal user input. And it is not related to 15.10 only but to all previous versions of Ubuntu.

In the 8 years I have been installing Ubuntu we have always been given the option to select the default language and never had the option to select more than one language during the installation process.

I, for one, do not want more user required options added to the installation process.

Regards.

---

