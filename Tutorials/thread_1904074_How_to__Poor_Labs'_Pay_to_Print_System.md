---
title: "How to:  Poor Labs' Pay to Print System"
date: 2012-01-04
forum: Tutorials
---

### Post by ethanay on 2012-01-04
This is my first how to.  Feel free to suggest improvements, but it is mostly offered as-is, with no warranty intended or implied, etc etc.  Hope it is a useful resource!

[SIZE="4"]Use Linux, room setup and program policy to make a Poor Labs' Pay to Print System[/SIZE]

**Impetus: **The public computer lab where I work exists on a shoe-string budget of less than $11,000.  The previous print setup was publicly-accessible.  Anyone could print at any time directly to any of the program's available printers.    The printing setup in the lab was subject to excessive problems and was a relatively large hole for money, time and other program resources.  However, the program is not able to acquire assistance to purchase an expensive, proprietary "pay to print" system.

So the question remains:  What to do to reduce and recover printing costs?  We had to take a multi-pronged approach:

[LIST=1]
[*]Move printers away from direct public access, to behind the administrative area, accessible only to program staff.
[*]Dedicate a printer (or two) to scratch paper, and collect good scratch paper (clean on one side; no wrinkles, tears or folds; no personal, private or confidential information) from the main office and nearby organizations or agencies.  Many places are happy to set aside their unused single-sided printouts as scratch paper.
[*]Make paying for print jobs mandatory
[*]Incentivize scratch paper use by making it less expensive (we charge 5 cents vs 10 cents for new paper printouts)
[*]We got rid of color printing -- if someone needs color or high quality graphics they need to take the job to a professional print service.
[*]Setup a Linux computer as a print server that directly shares only one printer
[*]Setup the lab computers to print to the print server by default, to allow staff the option of cancelling a job or moving it to a different printer
[*]The lock box where people put their donations and program service payments is in the same location where lab users go to pick up their printouts.
[/LIST]

**[SIZE="3"]Supplies needed:[/SIZE]**
[LIST]
[*]Two old monochrome laser printers in decent, reliable working order, capable of using generic PCL drivers
[LIST][*]One needs to be network-capable, with either a build-in print server or an external print server (e.g., JetDirect)
[/LIST]
[*]An extra computer system to use as the Lab Monitor's computer and the print server, to remain on and ready as long as the lab is open
[*]A clear print policy and set of guidelines and instructions for lab users and volunteers (see attached)
[LIST][*]PAGE 1.  the new print policy and procedures for lab users to print using new paper or scratch paper in the computer lab.
[*]PAGE 2.  the new Lab Monitor procedures and responsibilities.  You will follow these directions.
[/LIST]
[/LIST]

**Description:**  All computer lab print clients are connected to only one printer via the print server, which is set to hold jobs indefinitely.  The client computer uses a generic PCL 5 driver for compatibility, and the server passes the job through by either releasing the job to the default printer (e.g., new paper) or moving it to the secondary (e.g., scratch paper) printer, both of which use a generic raw print queue driver to be completely transparent.

[SIZE="3"]Setup details[/SIZE]

Printers in the Computer Lab are set up through a Linux-powered Print Server.  Printers are dedicated to either scratch paper or new paper, and labled as such  The following is how to set up and install the printers via the Linux Print Server, and then on Linux, Mac and Windows clients:

[SIZE="2"][B]Print server (Using Linux Mint 11)
[/B][/SIZE]
[LIST=1]
[*]Setup the computer to use a manual IP address.  In this case, the computer always uses 10.1.10.72
[*]Connect and install one printer to the print server using serial parallel port or USB.  Install the printer as normal.  Make sure this printer is NOT shared.
[*]Connect the second computer to the printer via its own network print server:  New printer, network printer, enter IP address of print server.  Make sure this printer is NOT shared.
[LIST][*]NOTE:  You may need to manually change to the correct driver after installation.  If they are outdated printers, they will need to use PCL instead of PostScript drivers.  For HP LaserJets, I recommend the Generic PCL 5e driver for consistency and simplicity.[/LIST]
[*]Once the local printers are set up, you are ready to print directly from the print server.  Use the “test page” function of the printer setup process to verify that they are working correctly as installed.
[*]Now you will need to recreate these same printers, but instead,
[LIST]
[*]Use the “Local Raw Printer” driver.  This allows the server to pass any print jobs it gets from client computers through directly to the printer
[*]Rename the printer “New-Paper-Raw” or “Scratch-Paper-Raw” respectively, depending on what type of paper it will use.  The printer name serves as the queue, which is needed to install the printers on the client computers.  Keeping the queues and IP addresses consistent means that we can theoretically change the printers connected to the server without worrying about having to update the client computers.
[*]Under ‘Job options,’ make sure that the printer is setup to “Hold indefinitely” by default.  This gives Lab Monitors the ability to choose whether, when and to which printer to release a print job.
[/LIST]
[*]You should now have four printers installed:  Two to function directly with the printer server, and two that the printer server will use.
[*]Now I configure Firefox to launch on startup, full screen, to localhost:631/jobs home page.  From here, volunteers can click the "jobs" tab to refresh the list when someone has printed, and learn whether to send it to scratch paper or new paper printer, and also say how much the printout costs.
[/LIST]

It's not perfect -- more ideally, there would be a non-web GUI front end that autorefreshes itself and monitors ALL print queues, but one does not exist yet.  Good news, though:  Something like this is [on its way]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/905528").

**[SIZE="2"]Linux client setup[/SIZE]**

[LIST=1]
[*]Add new network printer, search 10.1.10.72 host, choose "New-Paper-Raw" queue
[*]Finish, no test print
[*]Change driver > generic make (top of list) > PCL 5e foomatic ljet4
[*]Set as default printer
[/LIST]

**[SIZE="2"]Mac client setup[/SIZE]**

[LIST=1]
[*]Add new printer using IPP;  host: 10.1.10.72:631; queue: /printers/New-Paper-Raw
[*]Choose driver:  Generic PCL 5e Gutenprint
[*]Use print name New-Paper-Raw (this is more for consistency’s sake)
[*]Set as default printer
[/LIST]

**[SIZE="2"]Windows (XP) client setup[/SIZE]**

[LIST=1]
[*]Install HP Univeresal Print Driver (available from HP website).  The Add Printer dialogue should pop up automatically.
[*]Add new “network printer” (2nd option) select "connect via URL" (3rd option)
[*]Use the following URL:  [http://10.1.10.72:631/printers/New-Paper-Raw](http://10.1.10.72:631/printers/New-Paper-Raw)
[*]Driver:  choose "Have disk."  The installer from Step #1 above automatically unpacked the software and made it available via the dropdown menu.
[*]Select the HP Universal PCL5 package, choose the Universal Printing 5 driver
[*]Set as default printer, logout, and login to other accounts and set the new printer as default
[/LIST]

---

### Post by ethanay on 2012-05-02
Since writing this, we've revised our printer setup, which now has a multi-tray printer handling both scratch and new paper, a backup printer, and a color laser printer.

We've since learned that we don't need an additional raw printer on the server, which halves the number of printers installed on the server.  We accomplished this by outsourcing the printer selection and paper type to the participant:  they select either scratch paper or new paper or color printing (or the backup printer if necessary) and the Lab volunteer only needs to release or cancel the print job.

The updated setup eliminates the technical problem of transferring a print job between potentially-incompatible devices.  The new setup details and corresponding print policies and volunteer staff procedures are attached.

Pg 1 (7) are the instructions for program participants
Pg 2 (20) are the instructions for program volunteers
Pg 3-4 (38-39) are the technical setup and install notes for a system that has scratch paper, new paper, color and backup printing on Linux, Mac and Windows clients.

The basic idea is that all print jobs are routed through a second computer – the print server – for volunteer staff to approve or cancel.

---

### Post by ethanay on 2013-01-22
See attached for updates.  Updated text:

[LIST]
[*]Set up the print job administrative interface.  For us, this constitutes dedicated print queue windows launched on startup using the command:
[LIST]
[*]Edit the file ```
/etc/xdg/lxsession/autostart
``` and append the following command(s) using the syntax @command:  ```
@system-config-printer --show-jobs [printer name, e.g., HP-Color-LaserJet]
```  You can test this command (without the @ syntax) first via terminal to make sure it&#8217;s correct!
[*]If that is unavailable,  you can simply use a browser window that launches automatically on login in full-screen mode to the address ```
localhost:631/jobs/
```  Print admins will need to manually refresh the page with each new print job
[/LIST][/LIST]

---

