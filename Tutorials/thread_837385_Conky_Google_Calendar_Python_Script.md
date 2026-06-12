---
title: "Conky Google Calendar Python Script"
date: 2008-06-22
forum: Tutorials
---

### Post by kaivalagi on 2008-06-22
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

[COLOR="Blue"]_**[SIZE="4"]Intro[/SIZE]**_[/COLOR]

Following on from my conkyForecast script, I've created another which may be useful to you conky users out there. conkyForecast.py can be found here -> [http://ubuntuforums.org/showthread.php?p=5452132](http://ubuntuforums.org/showthread.php?p=5452132)

I have put together this python script to output Google Calendar events from a users default calendar, for use in Conky. I know there are already other means to do this using the command line, however I wanted something I could modify a little more, and will no doubt do so as and when I or you come up with new ideas.

Some key features
[LIST]
[*]Utilises the Google Calendar API.
[*]Supports the use of a template to define the layout of each event output
[*]Supports regional datetime formats, by way of system locales
[*]Optional event limit so you can reduce the total output in Conky if you have lot's of events, events should be returned earliest first (needs testing)
[/LIST]

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

Hope some of you find it useful

Any suggestions, please speak up!

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkygooglecalendar

```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyGoogleCalendar script to point to the correct location where conkyGoogleCalendar.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


[COLOR="Blue"]_**[SIZE="4"]Usage Help[/SIZE]**_[/COLOR]

You can get the current help options at any time by running (change the path as necessary):

```
conkyGoogleCalendar -h
```

or

```
conkyGoogleCalendar --help
```

The usage is as follows:

```
Usage: conkyGoogleCalendar [options]
Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        Username for login into Google Calendar, this will
                        normally be your gmail account
  -p PASSWORD, --password=PASSWORD
                        Password to login with, if not set the username is
                        used to fetch a 'conky' password from the keyring
  -r TEXT, --requestCalendarNames=TEXT
                        Define a list of calendars to request event data for,
                        calendar names should be separated by semi-colons ";".
                        For example --requestCalendarNames="cal1;cal2;other
                        cal" If not set all calendar data will be returned.
  -d NUMBER, --daysahead=NUMBER
                        [default: 7] Define the number of days ahead you wish
                        to retrieve calendar entries for, starting from today.
  -s DATE, --startdate=DATE
                        Define the start date to retrieve calendar events. In
                        the form '2007-12-01'
  -e DATE, --enddate=DATE
                        Define the end date to retrieve calendar events, must
                        be supplied if --startdate supplied. In the form
                        '2007-12-01'
  -a, --allevents       Retrieve all calendar events
  -w TEXT, --wordsearch=TEXT
                        Define the text to search calendar entries with.
  -l NUMBER, --limit=NUMBER
                        [default: 0] Define the maximum number of calendar
                        events to display, zero means no limit.
  -t FILE, --template=FILE
                        Template file determining the format for each event.
                        Use the following placeholders: [title], [starttime],
                        [endtime], [completetime], [duration], [location],
                        [description], [who]. Ensure only one placeholder per
                        line, as the whole line is removed if no data for that
                        placeholder exists.
  -f "DATEFORMAT", --dateformat="DATEFORMAT"
                        If used this overrides the default date formatting.
                        The values to use are standard formatting strings e.g.
                        Weekday=%a, Day=%d, Month=%m, Year=%y. For an output
                        like "Thu 15/10/2008" you would require
                        --dateformat="%a %d/%m/%y", to have no date you would
                        require --dateformat=""
  -F "TIMEFORMAT", --timeformat="TIMEFORMAT"
                        If used this overrides the default time formatting.
                        The values to use are standard formatting strings e.g.
                        Hours (12hr)=%l, Hours (24hr)=%H, Minutes=%M,
                        Seconds=%S, AM/PM=%P. For an output like "05:22 PM"
                        you would require --timeformat="%l:%M %P",
                        --timeformat="" is not supported, default locale
                        settings are used
  -i NUMBER, --indent=NUMBER
                        [default: 0] Define the number of spaces to indent the
                        output (excludes template based output)
  -m NUMBER, --maxwidth=NUMBER
                        [default: 40] Define the number of characters to
                        output per line
  -n, --nowho           Hides who is attending the events (excludes template
                        based output)
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 30] Define the number of seconds before a
                        connection timeout can occur.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

[COLOR="Blue"]_**[SIZE="4"]Gotchas[/SIZE]**_[/COLOR]

**Truncated Output**
Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size at the top of your conkyrc file, as follows:
```
text_buffer_size 512
```

**Captcha Issue**
The Google calendar function can stop working for with a "GoogleCalendarEngine Initialisation:Unexpected error:Captcha Required" error message. This is something Google enforces and to overcome it simple authenticate yourself here: [https://www.google.com/accounts/UnlockCaptcha](https://www.google.com/accounts/UnlockCaptcha)

**Locale and unicode support**
If you receive something similar to this error "ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)" it is because the script can't handle your locale settings for output.
To overcome this add the following above TEXT in your conkyrc:
```
override_utf8_locale yes
```

**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkygooglecalendar"]https://code.launchpad.net/~conky-companions/+junk/conkygooglecalendar
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by HippyRandall on 2008-06-22
more conky stuff to play with!!
:KS:KS:KS:KS:KS
soon my whole desktop is going to be full of conky output :lolflag:
keep up the good work kaivalagi

Hippy

---

### Post by Bruce M. on 2008-06-22
Oh oh ... I don't use Google Calendar but may have to start.  :)
Gotta go check it out now.

Good stuff kaivalagi, if this is half as good as your weather script it'll be very popular among the Google Calendar users.

Have a good day.
Bruce

**EDIT:** I'm a user now.  :)

---

### Post by pmaconi on 2008-06-22
Sounds cool. Could you post a screenshot?

---

### Post by kaivalagi on 2008-06-22
> **pmaconi said:**
> Sounds cool. Could you post a screenshot?

Screenshot added to the first post...

Edit: Noticed the first problem, events were not listed in date order...the google api must provide the events in the order they were created...Added a compare function to data class and sorted lists, earliest starttime first. Updated the first post :)

---

### Post by kaivalagi on 2008-06-23
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Just a couple of things done.

I have made sure that when using the --daysahead option to retrieve upcoming events, that no events are added that are from before the current datetime. Previously events from earlier the same day where also being output, this really isn't necessary as they're in the past.

I have also added an --indent option which when used will indent by how ever many spaces are specified. This doesn't work with the template option as spaces can be applied there instead.

[LIST]
[*]23/06/2008    Modified to only display current events (--daysahead option) that start after now
[*]23/06/2008    Added --indent option to add spaces to the front of each line that is output (excludes template output)
[/LIST]

Cheers

---

### Post by HippyRandall on 2008-06-23
now I am going to have to start getting organized and actually putting stuff on my gcalendar...boll ox (forums edit out the correct spelling)
:lolflag:

Hippy

---

### Post by kaivalagi on 2008-06-24
Guess what.....**[COLOR="Blue"][SIZE="3"]UPDATE[/SIZE][/COLOR]**

Done quite a bit more tonight, we now have details on who is attending the events by way of email addresses. This can also be turned off using a new --nowho option. I have also fixed up the template functionality to remove unwanted whitespace only lines from the output, for situations where not all the data is available for an event.

Also done a general tidy up of the code, and put in some tweaks to make event listings generally more sensible, including having re-occuring events treated like multiple single events.

What went onto the dev history:
[LIST]
[*]24/06/2008    Added who is attending (email addresses) to the output of each event, added a <who> parameter for the template, and added a --nowho option to hide the data (excludes template output)
[*]24/06/2008    Fixed up template output using regex, to remove unnecessary blank lines where no data exists
[/LIST]

Cheers,
Mark

---

### Post by HippyRandall on 2008-06-24
You've been busy! Nice additions. I am in the process of adding events to my calendar to test some of this stuff out.
Keep coming with the new ideas!

Hippy

---

### Post by PurposeOfReason on 2008-06-30
Quite nice. Do you think it will be possible to align things left and right?

---

### Post by kaivalagi on 2008-07-01
> **PurposeOfReason said:**
> Quite nice. Do you think it will be possible to align things left and right?

I'll have to think on that one!

The alignment ideally should be done in conky, so splitting up the details as separate pieces of data will be needed.

To do that I'll need to fetch all the event data upfront, cache it locally, and then have some way of picking each bit using script options in separate execi calls...

It would mean rewriting the current functionality altogether...I think

---

### Post by martynp on 2008-07-06
Hi Mate,

Love all the changes and additions to the weather script and this one is good too!

Now the BIG challenge................

Google Reader in Conky!!!!!!!!!!!!!!

Regards,

Martyn

---

### Post by kaivalagi on 2008-07-06
> **martynp said:**
> Hi Mate,

Love all the changes and additions to the weather script and this one is good too!

Now the BIG challenge................

Google Reader in Conky!!!!!!!!!!!!!!

Regards,

Martyn

I've been pondering over a decent rss reader, the one that comes with conky is really slow, for each feeds article it hits the web, rather than bringing back say 10 of the articles from a feed and showing those....

The gdata api doesn't currently support google reader, but I could create my own equivalent for any rss url's....?

---

### Post by martynp on 2008-07-08
How about finding a way to show the number of unread items in Google Reader.

This app does it standalone in the taskbar.

[http://grnotify.sourceforge.net/](http://grnotify.sourceforge.net/)

but it would be great to see the info (unread item count alone would be enough) in Conky?

Regards,

Martyn

---

### Post by kaivalagi on 2008-07-08
> **martynp said:**
> How about finding a way to show the number of unread items in Google Reader.

This app does it standalone in the taskbar.

[http://grnotify.sourceforge.net/](http://grnotify.sourceforge.net/)

but it would be great to see the info (unread item count alone would be enough) in Conky?

Regards,

Martyn

If someone could spare a month doing it, it may be possible using the grnotify python code as a basis to talk to the xml based google reader api...the example code isn't really what we want for conky. The trouble I see is that grnotify brings back html content and displays it like a browser would, we can't do that in Conky! We need plain text, so we'd have to strip all the content out...far too much bother! really! 

I guess a simple count function could be done relatively quickly...maybe adapted from the conkyemail script I created?

It really is a shame that there isn't a gdata api for it, it's some much more powerful that way.

---

### Post by martynp on 2008-07-09
Hi,

Just showing the amount of unread items would be cool.

Have been using the grNotify app but it has some issues so I have given up on it.

Any way of doing a simple script to show unread item count like with email?

Pretty pleaaaaaaaase!

Martyn

---

### Post by kaivalagi on 2008-07-09
> **martynp said:**
> Hi,

Just showing the amount of unread items would be cool.

Have been using the grNotify app but it has some issues so I have given up on it.

Any way of doing a simple script to show unread item count like with email?

Pretty pleaaaaaaaase!

Martyn

Okay, okay, okay :)

I have something nearly there...bloody google require cookie authentication for this which was a bit%h to sort out nicely, but got it working....

Right now I can bring back the xml which contains the unread items e.g.:

```
<object>
    <number name="max">1000</number>
    <list name="unreadcounts">
        <object>
            <string name="id">feed/http://www.usp.ac.fj/news/rss.php</string>
            <number name="count">9</number>
            <number name="newestItemTimestampUsec">1215032380461011</number>
        </object>
        <object>
            <string name="id">feed/http://www.fijitimes.com/rss.aspx?section=local</string>
            <number name="count">1000</number>
            <number name="newestItemTimestampUsec">1215582131344330</number>
        </object>
        ...
    </list>
</object>
```

You can tell I haven't used google reader in a while...

From this I can give a general count on how many feeds have unread items and display each feed and it's unread count. Which way do you want it?

They need beer tokens on the net redeemable at any good off-licence :)

[COLOR="Blue"]**[SIZE="3"]EDIT[/SIZE]**[/COLOR]

I've attached the script, general help below:

```
Usage: conkyGoogleReader.py [options]

Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        username to login with
  -p PASSWORD, --password=PASSWORD
                        Password to login with
  -v, --verbose         request verbose output, not a good idea when running
                        through conky!
```

So in conky you would use something like this (haven't tried it in conky, just in eclipse (dev ide)):

```
{execi 1800 python conkyGoogleReader.py --username=someone@gmail.com --password=something}
```
Give your email and password for your google account and it should come back with something like "5 Unread Feeds"

[COLOR="Blue"]Edit2: updated script in latest post!/COLOR]

---

### Post by HippyRandall on 2008-07-09
***dreams fitfully of a desktop that supports html and clickable links in conky
................................................html
....................................click
...................................html
***

wakes up and realizes it was all a dream and smashes head against keyboards](*,)

:lolflag:

---

### Post by kaivalagi on 2008-07-09
> **HippyRandall said:**
> ***dreams fitfully of a desktop that supports html and clickable links in conky
................................................html
....................................click
...................................html
***

wakes up and realizes it was all a dream and smashes head against keyboards](*,)

:lolflag:

No dreams for me :(

I have nightmares about formatting plain text in conky, and it never lining up well enough!

Forever the optimist :mrgreen:

---

### Post by martynp on 2008-07-10
Morning,

Thanks so much for working on this!!! It is truly appreciated.

I have tried the script and it is basically returning the pure XML as shown in your code and not formatting it in any way. I think I have all correct.

Also, from a personal note, I would be happy with just the total number of unread feeds in my google account as I have around 600 different ones in total. That would take a LOT of screen space with your current formatting!

Sorry for the lack of screenshot but just off to the dentist. I will be at home the rest of the day and tomorrow though.

Thanks mate.

*** I'll post a screenie and what output I am getting in about an hour or so ***

---

### Post by martynp on 2008-07-10
I managed to do one.... see attached


****** LOL********

Not attached. That will teach me to rush.... see next post

---

### Post by martynp on 2008-07-10
I managed to do one... see attached  :)

EDIT

Further to this I ran the command in a terminal and am posting the output below in case it helps. Also, I believe the count should be unread 'Items' and not 'Feeds'.

Thanks again for your hard work!

Also... sorry, I don't seem to able to post this output in a 'box'

Here it is:

**<object>
    <number name="max">1000</number>
    <list name="unreadcounts">
        <object>
            <string name="id">feed/http://www.impactwrestling.com/rss.aspx</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/label/News</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/label/Ubuntu</string>
            <number name="count">7</number>
            <number name="newestItemTimestampUsec">1215685798064474</number>
        </object>
        <object>
            <string name="id">feed/http://www.ubuntuhq.com/rss.xml</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685798064474</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/state/com.google/reading-list</string>
            <number name="count">8</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">feed/http://www.gnome-look.org/gnome-look-content.rdf</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685409813364</number>
        </object>
        <object>
            <string name="id">feed/http://ubuntu.hamdi.web.id/feed</string>
            <number name="count">5</number>
            <number name="newestItemTimestampUsec">1215425742525315</number>
        </object>
    </list>
</object>

countlist: [<DOM Element: number at 0x8373dec>, <DOM Element: number at 0x837b1ac>, <DOM Element: number at 0x837b2cc>, <DOM Element: number at 0x837b54c>, <DOM Element: number at 0x8368a6c>, <DOM Element: number at 0x837b5cc>, <DOM Element: number at 0x837b6ec>, <DOM Element: number at 0x837b96c>, <DOM Element: number at 0x837ba8c>, <DOM Element: number at 0x837bd0c>, <DOM Element: number at 0x837be2c>, <DOM Element: number at 0x83810cc>, <DOM Element: number at 0x83811ec>, <DOM Element: number at 0x838146c>, <DOM Element: number at 0x838158c>]
6 Unread Feeds

---

### Post by kaivalagi on 2008-07-10
> **martynp said:**
> I managed to do one... see attached  :)

EDIT

Further to this I ran the command in a terminal and am posting the output below in case it helps. Also, I believe the count should be unread 'Items' and not 'Feeds'.

Thanks again for your hard work!

Also... sorry, I don't seem to able to post this output in a 'box'

Here it is:

**<object>
    <number name="max">1000</number>
    <list name="unreadcounts">
        <object>
            <string name="id">feed/http://www.impactwrestling.com/rss.aspx</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/label/News</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/label/Ubuntu</string>
            <number name="count">7</number>
            <number name="newestItemTimestampUsec">1215685798064474</number>
        </object>
        <object>
            <string name="id">feed/http://www.ubuntuhq.com/rss.xml</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685798064474</number>
        </object>
        <object>
            <string name="id">user/06078103049471248256/state/com.google/reading-list</string>
            <number name="count">8</number>
            <number name="newestItemTimestampUsec">1215685823786973</number>
        </object>
        <object>
            <string name="id">feed/http://www.gnome-look.org/gnome-look-content.rdf</string>
            <number name="count">1</number>
            <number name="newestItemTimestampUsec">1215685409813364</number>
        </object>
        <object>
            <string name="id">feed/http://ubuntu.hamdi.web.id/feed</string>
            <number name="count">5</number>
            <number name="newestItemTimestampUsec">1215425742525315</number>
        </object>
    </list>
</object>

countlist: [<DOM Element: number at 0x8373dec>, <DOM Element: number at 0x837b1ac>, <DOM Element: number at 0x837b2cc>, <DOM Element: number at 0x837b54c>, <DOM Element: number at 0x8368a6c>, <DOM Element: number at 0x837b5cc>, <DOM Element: number at 0x837b6ec>, <DOM Element: number at 0x837b96c>, <DOM Element: number at 0x837ba8c>, <DOM Element: number at 0x837bd0c>, <DOM Element: number at 0x837be2c>, <DOM Element: number at 0x83810cc>, <DOM Element: number at 0x83811ec>, <DOM Element: number at 0x838146c>, <DOM Element: number at 0x838158c>]
6 Unread Feeds

Apologies, I left in the print statements from my debugging!

The last line is the only thing that should be output! :)

---

### Post by martynp on 2008-07-10
Hi,

That, of course, worked perfectly.

Thanks SO much, however, (and there is always one!) is it possible to show the unread ITEMS instead of FEEDS?

I would guess this is a fairly simply change to just count the number of unread items in each feed and output a grand total.

Of course..... it could be taken even further but the above would be wonderful!!

Thanks,

Martyn

EDIT

Actually I am wondering if it IS in fact showing unread item and you have just called them feeds in the script?

EDIT 2

As I type google reader tells me I have 31 unread items and your script is saying 19

---

### Post by kaivalagi on 2008-07-10
> **martynp said:**
> 
As I type google reader tells me I have 31 unread items and your script is saying 19

Should be 19 feeds with unread items...does that not sound right?

I'll play some more with it at the weekend, a grand total of unread items should be possible with minimal effort :)

---

### Post by martynp on 2008-07-10
Hi,

Thanks for the reply.

At 8pm I have 32 feeds with 153 unread items.

The script is showing 40 unread feeds.

Your time and effort is greatly appreciated.

Thanks,

Martyn

---

### Post by kaivalagi on 2008-07-10
> **martynp said:**
> Hi,

Thanks for the reply.

At 8pm I have 32 feeds with 153 unread items.

The script is showing 40 unread feeds.

Your time and effort is greatly appreciated.

Thanks,

Martyn

I've updated the script again, attached here this time...

It now outputs unread feeds, unread items total and each feed with the unread amount of items.

In the script you'll see the following section of code:
```
        print "%s Unread Feeds" % unreadfeedscount
        print "%s Unread Items" % unreaditemtotalcount
        for (unreaditemcount, feedurl) in feeds:
            print "%s - %s Unread Items" % (feedurl, unreaditemcount)
```

To only output what you want just comment out the print statements that aren't needed. e.g. if you only want unread items it would be like this:

```
        #print "%s Unread Feeds" % unreadfeedscount
        print "%s Unread Items" % unreaditemtotalcount
        #for (unreaditemcount, feedurl) in feeds:
            #print "%s - %s Unread Items" % (feedurl, unreaditemcount)
```

Have a play and let me know where things are not adding up :)

We can sort out the options to pick what you want to output later on, if it works properly...

[COLOR="Blue"]**EDIT: **[/COLOR]The counts are good for me now...not sure whether it will work for you now?

New datatype option, help below:
```
Usage: conkyGoogleReader.py [options]

Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        username to login with
  -p PASSWORD, --password=PASSWORD
                        Password to login with
  -v, --verbose         request verbose output, not a good idea when running
                        through conky!
  -d DATATYPE, --datatype=DATATYPE
                        (default: [UI] datatype to retreive, UF (unread
                        feeds), UI (unread items), UL (unread feeds list)
```

---

### Post by martynp on 2008-07-11
Morning,

Thanks for this. In essence it works.

However, I think you have doubled the unread feeds somewhere as this morning I am showing 253 unread items and the script shows 506.

There is still a discrepancy in the number of unread feeds. My 253 unread items are in 27 feeds and the script is showing 35 as the number of unread feeds.

I can confirm that the printing of the url's and number of unread items appears to work fine.

Definately getting there. If I anything about programming I would look in the script myself as I am sure the 'doubling up' is something simple but not sure about the discrepancy in the unread feeds count.

Thanks again and I look forward to hearing back from you when you have the time.

Martyn

---

### Post by kaivalagi on 2008-07-11
> **martynp said:**
> Morning,

Thanks for this. In essence it works.

However, I think you have doubled the unread feeds somewhere as this morning I am showing 253 unread items and the script shows 506.

There is still a discrepancy in the number of unread feeds. My 253 unread items are in 27 feeds and the script is showing 35 as the number of unread feeds.

I can confirm that the printing of the url's and number of unread items appears to work fine.

Definately getting there. If I anything about programming I would look in the script myself as I am sure the 'doubling up' is something simple but not sure about the discrepancy in the unread feeds count.

Thanks again and I look forward to hearing back from you when you have the time.

Martyn
No problem, now we have a sort of working script, it's easy to tweak it...

I've updated the attachment on the previous post, details there too

---

### Post by martynp on 2008-07-11
Hi,

Confirming the new script installed. Formatting (ie datatype) working fine but everything is still getting doubled up.

As I am watching I have 6 unread items in 5 feeds.

The script is showing 12 unread items in 10 feeds.

I have it refreshing every 60 seconds and am refreshing google reader AND grNotify at the same time to ensure accuracy.

See the attached screenshot and note the unread feed count in grNotify in the system tray. This is the correct number.

Martyn

---

### Post by kaivalagi on 2008-07-11
> **martynp said:**
> Hi,

Confirming the new script installed. Formatting (ie datatype) working fine but everything is still getting doubled up.

As I am watching I have 6 unread items in 5 feeds.

The script is showing 12 unread items in 10 feeds.

I have it refreshing every 60 seconds and am refreshing google reader AND grNotify at the same time to ensure accuracy.

See the attached screenshot and note the unread feed count in grNotify in the system tray. This is the correct number.

Martyn

I think it might have something to do with the user entries, e.g. in your xml there are several entries like this:

```
user/06078103049471248256/label/News
```

They seem to be user defined categories. So when the script is counting the totals up, it is doing so based on the feeds and the categories, hence the doubling up. The reason I didn't get this problem is 'cause I don't have any categories defined.

New script attached which ignores the user category counts for now, let me know whether the results are good now :)

Fingers crossed!

[COLOR="Blue"]Edit: If this doesn't work you're going to have to PM me your feeds xml, just paste this into your browser to get it: [https://www.google.com/reader/api/0/unread-count?all=true](https://www.google.com/reader/api/0/unread-count?all=true)[/COLOR]

---

### Post by martynp on 2008-07-11
Hi,

Appears to work like a charm!!!

I'll monitor for a few hours and let you know if any problems!

Thanks you soooooooo much! :KS

---

### Post by imjscn on 2008-07-14
Is it possible to use Conky and your google api tech to get any information from any website?
I wish to get this public calenda in Conky:
[http://www.forexfactory.com/calendar.php?](http://www.forexfactory.com/calendar.php?)

---

### Post by kaivalagi on 2008-07-14
> **imjscn said:**
> Is it possible to use Conky and your google api tech to get any information from any website?
I wish to get this public calenda in Conky:
[http://www.forexfactory.com/calendar.php?](http://www.forexfactory.com/calendar.php?)

Currently it only handles your primary calendar in google, and it will never handle any calendar data not within the google umbrella as it were.

It may be possible to source calendar data from a public google calendar instead of your own, but it will require investigation before I can say yes for certain.

The calendar you are referencing looks like it's a custom one created for that website which will not work at all with the gdata api used in my script. However if you can find a google public calendar which represents that link then it might be possible...the company would need this setup unfront...I can't see any links to one from the website...

Hope that answers your question :)

---

### Post by imjscn on 2008-07-14
kaivalagi. thanks for look into this.
No, there are no google puclic calendar represents this link in full because people just take a part that in their interest to their google calendar. But I need it in full. 
Now I understand how this tech works. Maybe I just import this calendar into my google calenda, then, implement your tech to get it in conky.
Thanks!

---

### Post by eriqjaffe on 2008-07-15
kaivalagi, thanks a million for this!  I had a very clunky script using gcalcli, but this provides for far more elegant output.

Two things I might suggest:

1) The ability to not display the time on "All Day" events.  I have added this into the code (in the "Formatting Functions" section, and it does the trick for me.  Granted, this would filter out any task starting at midnight, but...

```
starttime = starttime.replace("12:00:00 AM","")
```

2) Probably an easy thing to add, but I can't quite figure out where.  If there are no tasks, return a string like "No tasks found."

Otherwise, this is absolutely fantastic!

---

### Post by kaivalagi on 2008-07-16
> **eriqjaffe said:**
> 
1) The ability to not display the time on "All Day" events.  I have added this into the code (in the "Formatting Functions" section, and it does the trick for me.  Granted, this would filter out any task starting at midnight, but...

```
starttime = starttime.replace("12:00:00 AM","")
```


For the all day task it should be returning no time field already? When an all day event comes through it has no time aspect, which I make sure doesn't show using getDateFromWhen function. There must be certain circumstances where this is not always the case. I'll add some further checks for range between start and end datetime, when it is a full day I'll make sure no time is shown.

Can you tell we what the date format comes through as for you? DD/MM/YYYY HH:MM:SS etc? The script is locale based...that might have some effect also?

> **eriqjaffe said:**
> 
2) Probably an easy thing to add, but I can't quite figure out where.  If there are no tasks, return a string like "No tasks found."


This one should be easy enough, I just need to add a check for the length of the event list that comes back, and if zero print "No tasks found"

Let me know what the format of the datetime is for you, and I'll then get this sorted over the next couple of days...

Glad you find the script useful :)

Cheers

---

### Post by eriqjaffe on 2008-07-18
Here's what I get with raw output from the script - all the events in the calendar are "all day" events:

```
eriq@eriq-ubuntu:~/cgc$ python conkyGoogleCalendar.py --username=*****@gmail.com --password=***** --daysahead=7
Title: Do checking
Start Time: Mon 21 Jul 2008 12:00:00 AM 
End Time: Tue 22 Jul 2008 12:00:00 AM 
Who: *****@gmail.com

Title: Mail mortgage
Start Time: Wed 23 Jul 2008 12:00:00 AM 
End Time: Thu 24 Jul 2008 12:00:00 AM 
Who: *****@gmail.com
```

You mentioned that it's locale based, and that could be the issue, since we're on different sides of the Atlantic.

---

### Post by kaivalagi on 2008-07-19
> **eriqjaffe said:**
> Here's what I get with raw output from the script - all the events in the calendar are "all day" events:

```
eriq@eriq-ubuntu:~/cgc$ python conkyGoogleCalendar.py --username=*****@gmail.com --password=***** --daysahead=7
Title: Do checking
Start Time: Mon 21 Jul 2008 12:00:00 AM 
End Time: Tue 22 Jul 2008 12:00:00 AM 
Who: *****@gmail.com

Title: Mail mortgage
Start Time: Wed 23 Jul 2008 12:00:00 AM 
End Time: Thu 24 Jul 2008 12:00:00 AM 
Who: *****@gmail.com
```

You mentioned that it's locale based, and that could be the issue, since we're on different sides of the Atlantic.

This is going to be a tricky one, I've attached an updated script to include "12:00:00 AM" as something to strip out when converting date only data to a string...hopefully that will sort it. For my locales, the system converts a date only datetime type to a string with "00:00:00" on the end instead, which I already catered for.

I'm assuming that the all day events have been added via google calendar itself and not from a sync for another client such as outlook? If this is the case you might want to check the difference for output between an all day event created directly in Google calendar to this one, it might explain things?

Could you also run the attached python script called dateformat.py, it will tell us what your locale settings are.

Even if the main script change fixes the issue I'd like to know what the output is, as it might help me understand other issues around the corner.

Mine comes out with:
```
datetimeformat:%a %d %b %Y %T %Z
dateformat:%d/%m/%y

```

From all this we _should_ have a good idea of the problem

Why couldn't we all just use the same date time formatting! You guys over the Atlantic have to be different :-P

I've also added a check for any events, if non are found then it just outputs "No Events...".

When this all checks out I'll update the first post

---

### Post by eriqjaffe on 2008-07-21
The udpated script does the trick (for me, at least) without having to modify anytyhing, thanks!

All of the events were added directly to the Google Calendar as recurring all-day events via Google's web interface.  I haven't tried using other methods (I know events can be added via gcalcli, for example), so I don't know how they will wind up displaying.

And, sure enough, my date & time formats are different:

```
datetimeformat:%a %d %b %Y %r %Z
dateformat:%m/%d/%Y
```

Thanks again, hope that information comes in handy.

---

### Post by kaivalagi on 2008-07-21
> **eriqjaffe said:**
> The udpated script does the trick (for me, at least) without having to modify anytyhing, thanks!

All of the events were added directly to the Google Calendar as recurring all-day events via Google's web interface.  I haven't tried using other methods (I know events can be added via gcalcli, for example), so I don't know how they will wind up displaying.

And, sure enough, my date & time formats are different:

```
datetimeformat:%a %d %b %Y %r %Z
dateformat:%m/%d/%Y
```

Thanks again, hope that information comes in handy.

Nice one, glad it worked.

I'll take a look at the date format stuff soon, to make sure no other formats will be affected...

---

### Post by kaivalagi on 2008-07-21
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

Updated the script in the first post, see below or first post for details.

[LIST]
[*]Output "No Events..." if non found, rather than nothing at all.
[*]Fix for all day events where time is shown. Catered for 12:00:00 AM (%r formatted time) so it is no longer displayed.
[/LIST]

Cheers

---

### Post by kaivalagi on 2008-07-21
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][SIZE="1"] (AGAIN)[/SIZE][/COLOR]**

Updated date time formatting, datetime now formatted using Day + locale.D_FMT + locale.T_FMT_AMPM, date only uses Day + locale.D_FMT. In my locale this results in the format "Wed 15/02/2007 13:00:00 pm", for US users the day number and month will be switched :)

This results in a much more consistent approach to date time formatting which, no matter what the formatting options, the event data should show correctly and consistently for your regional settings.

New script uploaded to the first post.

Cheers

[COLOR="Blue"]Edit: Just added Day to the formatting too, first post script updated...[/COLOR]

---

### Post by HippyRandall on 2008-07-21
> **kaivalagi said:**
> **[COLOR=Blue][SIZE=4]UPDATE[/SIZE][SIZE=1] (AGAIN)[/SIZE][/COLOR]**
In my locale this results in the format "15/02/2007 13:00:00 pm"
Someone needs to sync their time/date with a time server! 
:lolflag::lolflag::lolflag:

Sorry but I couldn't resist

Hippy Randall

---

### Post by kaivalagi on 2008-07-21
> **HippyRandall said:**
> Someone needs to sync their time/date with a time server! 
:lolflag::lolflag::lolflag:

Sorry but I couldn't resist

Hippy Randall

I am living in the past like so many windoze users :)

---

### Post by jmadero on 2008-07-30
Hi All,

This is a great conky script...but I'm having one problem.

I can't get more than 1 event to show no matter what I do. I've tried making the end date the end of the year, making the daysahead = 5...etc..

Even when I have more than one event on the same day it's only showing one. 

Any help would be appreciated. Thanks!

---

### Post by kaivalagi on 2008-07-30
> **jmadero said:**
> Hi All,

This is a great conky script...but I'm having one problem.

I can't get more than 1 event to show no matter what I do. I've tried making the end date the end of the year, making the daysahead = 5...etc..

Even when I have more than one event on the same day it's only showing one. 

Any help would be appreciated. Thanks!

Could you post the execi line from your conkyrc (minus your login details :))

Are all your events reoccurring ones?
Do you add the events straight into google calendar or are they sync'ed from a client app?
Do you have a --limit option set?

This is going to be tricky to debug cause I can't test against your calendar...would it be possible to recreate the events (minus the details) on a calendar you can give me full access to?

---

### Post by jmadero on 2008-07-30
Here is the line from my conky script:

${execi 10800 python ~/.conky/Calendar/conkyGoogleCalendar.py --username=XXX@gmail.com --password=XXX --daysahead=5 --limit=10}

Most of my things are recurring, but I did put in a test single event for today and it only showed the recurring event happening at 2 PM (the new event was set for 5 PM)

I enter events directly into google calendar (google plugin for thunderbird has issues from the repos so I just go direct)

limit is set to 10 


Thanks for the help

---

### Post by kaivalagi on 2008-07-30
> **jmadero said:**
> Here is the line from my conky script:

${execi 10800 python ~/.conky/Calendar/conkyGoogleCalendar.py --username=XXX@gmail.com --password=XXX --daysahead=5 --limit=10}

Most of my things are recurring, but I did put in a test single event for today and it only showed the recurring event happening at 2 PM (the new event was set for 5 PM)

I enter events directly into google calendar (google plugin for thunderbird has issues from the repos so I just go direct)

limit is set to 10 


Thanks for the help

Everything seems okay

To eliminate conky out of the equation can you run the script in the terminal, e.g.

```
python ~/.conky/Calendar/conkyGoogleCalendar.py --username=XXX@gmail.com --password=XXX --daysahead=5 --limit=10
```

Do you still only get one event back?

If you see everything you expect in the terminal, you may need to add the following before the TEXT section in your conkyrc:

```
text_buffer_size 512
```

Keep increasing the value until you see everything you want to.

Long shot but this has been the cause of many an issue in conky in the past.....

---

### Post by jmadero on 2008-07-30
solved :) it was the buffer. Thanks!

---

### Post by kaivalagi on 2008-07-30
> **jmadero said:**
> solved :) it was the buffer. Thanks!

Glad it's working :)

---

### Post by PurposeOfReason on 2008-07-30
Would a simple grep be able to shorten things out such as start and end times? I really don't need to know things like the year and day of the week. 

Thanks.

---

### Post by kaivalagi on 2008-07-30
> **PurposeOfReason said:**
> Would a simple grep be able to shorten things out such as start and end times? I really don't need to know things like the year and day of the week. 

Thanks.

Currently the script formats the datetime of events to whatever your system default is. Obviously though this won't do you any good, cause changing a datetime format on your system to show just the time would be a bit limiting in general :)

Using grep in this scenario would be really tricky. The output is for multiple events and all thier data so some form of regex using "sed" would be needed I think. I guess it could be done using a bash script which then calls the python script but...

I think the best approach for differing datetime formats would be an command line option which overrides the current behaviour, maybe a --timeonly option? or even a --datetimeformat= which could be used like this:

--format=%H:%M %p for 09:42 PM
--format=%D/%m/%Y for 31/07/2008

etc etc

If we took this approach it would fit nicely into the datetime formatting function which already exists in the script, which handles the default system locale settings.

Can you think through the possible formatting that you would like to see, i.e. a 1 hour meeting, an all day event etc. Let me know what you'd expect and I'll think through the possibilities and a way round them...(what if an event starts late one evening and finishes the next morning, would the date part still not be needed?)

Interesting request!

---

### Post by PurposeOfReason on 2008-08-01
The formatting I think would be useful would be something alone the lines of 

08/01 7:00PM - 08/01 8:30PM

or if somehow the script could be "aware" that the even was on the same day, just

08/01 7:00PM - 8:30PM

---

### Post by kaivalagi on 2008-08-02
> **PurposeOfReason said:**
> The formatting I think would be useful would be something alone the lines of 

08/01 7:00PM - 08/01 8:30PM

or if somehow the script could be "aware" that the even was on the same day, just

08/01 7:00PM - 8:30PM

Having the date only showing at the front of the start and end dates will not be simple, so I'll give that one a miss.

I think the best way forward is to provide overriding formatting for a datetime so a user can define it how they want to, based on standard formatting strings.

I hope that works for you (and anyone else :))

An updated script will be available soon...

[COLOR="Blue"]**Edit:**[/COLOR] For you to have this output:

```
08/01 7:00PM - 08/01 8:30PM
```

Set the --dateformat option as follows:

```
--dateformat="%d/%m"
```

That's if it is day then month?

The output time part will remain as it was before.

---

### Post by kaivalagi on 2008-08-02
[COLOR="Blue"][SIZE="4"][B]UPDATE
[/B][/SIZE][/COLOR]

I've added a --dateformat option which will change the way event dates are displayed.

--dateformat="%d/%m" would output "02/07"
--dateformat="%a" would output "Sat"
--dateformat="%m/%d/%y" would output "07/02/2008"
--dateformat="" would output no date info
etc etc

If the option is not used the default locales settings will be used, as previously setup.

The help on this option is as follows:

```
  -f DATEFORMAT, --dateformat=DATEFORMAT
                        If used this overrides the default date formatting.
                        The values to use are standard formatting strings e.g.
                        Weekday=%a, Day=%d, Month=%m, Year=%y. For an output
                        like this "Thu 15/10/2008" you would require
                        --dateformat="%a %d/%m/%y", to have no date you would
                        require --dateformat=""
```

I've updated the script which is available in the first post

Cheers

---

### Post by PurposeOfReason on 2008-08-02
Thank you, it works great with what I want. Just being super picky, can seconds be removed? lol

---

### Post by kaivalagi on 2008-08-03
> **PurposeOfReason said:**
> Thank you, it works great with what I want. Just being super picky, can seconds be removed? lol


Cool, I just updated the script again, there was a small bug with the date formatting code...

---

### Post by vasilub1 on 2008-08-23
> **kaivalagi said:**
> Cool, I just updated the script again, there was a small bug with the date formatting code...

Hi, kaivalagi, 
I am a new one here and a beginner... I added here my modest contribution to your WeatherPythonScript. Please tell me if is OK and if is useful...
I informed also Bruce M.
All the Best !

---

### Post by kaivalagi on 2008-08-23
> **vasilub1 said:**
> Hi, kaivalagi, 
I am a new one here and a beginner... I added here my modest contribution to your WeatherPythonScript. Please tell me if is OK and if is useful...
I informed also Bruce M.
All the Best !

Thanks for that, although you didn't post on the correct thread, and things have changed in relation to translations recently. Use the link from my signature to get to the right thread

Have a good look at the first post, things have moved on since you last looked at the script. We now have apt based installs and translations are not done in the script, they are done using a tool called poedit, which helps you create .po/.mo files for inclusion in a release. No one needs to change the script code anymore :)

Any questions just post on the weather script thread which my signature links to...a number of users on there have been through this translation process, including Bruce

Your translation is very much welcome, we just need it in the correct format :)

I hope you understand

Thanks

---

### Post by vasilub1 on 2008-08-23
> **kaivalagi said:**
> Thanks for that, although you didn't post on the correct thread, and things have changed in relation to translations recently. Use the link from my signature to get to the right thread

Have a good look at the first post, things have moved on since you last looked at the script. We now have apt based installs and translations are not done in the script, they are done using a tool called poedit, which helps you create .po/.mo files for inclusion in a release. No one needs to change the script code anymore :)

Any questions just post on the weather script thread which my signature links to...a number of users on there have been through this translation process, including Bruce

Your translation is very much welcome, we just need it in the correct format :)

I hope you understand

Thanks


OK, Thank you for updates...
I will try ...

---

### Post by Technoviking on 2008-08-25
Reoccurring meetings don't show up with this script. Does anyone else have this problem?

---

### Post by kaivalagi on 2008-08-25
> **Mike said:**
> Reoccurring meetings don't show up with this script. Does anyone else have this problem?

Hi Mike, can you tell me which options you are using?

I thought I had it covered, the gdata api has an option to return reoccurring events as separate single ones...which I thought I'd implemented

It's been a while since I messed with this script properly, so some pointers to reproduce the problem would be useful. I can then setup some fake events in my calendar and step through the code.

[COLOR="Blue"]Edit: had a quick look through the script, and I have the option "query.singleevents = 'true'" for all data retrieval, except --allevents as this proved a problem. Is this the option you are using when getting the problem? *fingers crossed*[/COLOR]

---

### Post by Technoviking on 2008-08-25
```
--allevents --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template
```
If I don't have --allevents, I don't get anything from my calendar.

---

### Post by kaivalagi on 2008-08-25
> **Mike said:**
> ```
--allevents --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template
```
If I don't have --allevents, I don't get anything from my calendar.

As the code does a date check , ignoring start dates before "now" you will not see reoccurring events setup before "now".....which will be the vast majority I would imagine. I will change it to check against the end date instead...which makes more snese anyway...what if you have a holiday which started yesterday but will be going on for a week, currently you won't see it for --allevents.

Knowing that the other options return nothing for you, highlights another problem with query options maybe...but it could be default settings...

Try switching --allevents for --daysahead=n, where n is the number of days. If you ran your options above without --allevents you'd only receive the next 24 hours of events as that's the default. Set --daysahead=7 for the next 7 days for example. I would hope you get something back...e.g.
```
--daysahead=7 --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template
```

Anyway, update to come shortly which hopefully sorts out your issues with the script with you needing to change the settings

---

### Post by kaivalagi on 2008-08-25
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

Couple of changes to the script which should stop some issues...

[LIST]
[*]Events now get ignored when their end date is not effective anymore, rather than the start date
[*]Changed default for --daysahead from 1 to 7, and up'ed the default for the end date parameter of date ranged output, now up to the year 2020
[/LIST]

New script attached to the first post...

---

### Post by Technoviking on 2008-08-26
Getting the following error.
```
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 493, in <module>
    main()
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 482, in main
    output = googleCalendarEngine.getTemplateOutput(template, title, starttime, endtime, location, description, who)
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 308, in getTemplateOutput
    output = output.replace("<who>",who)
TypeError: expected a character buffer object

```

---

### Post by kaivalagi on 2008-08-26
> **Mike said:**
> Getting the following error.
```
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 493, in <module>
    main()
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 482, in main
    output = googleCalendarEngine.getTemplateOutput(template, title, starttime, endtime, location, description, who)
  File "/home/dbasinge/conky/conkyGoogleCalendar.py", line 308, in getTemplateOutput
    output = output.replace("<who>",who)
TypeError: expected a character buffer object

```

Another update...see first post for the fix

This is the best testing this has ever had!

Never trust a developer to test his own work :)

---

### Post by Technoviking on 2008-08-26
Working great.:popcorn:

---

### Post by kaivalagi on 2008-08-26
> **Mike said:**
> Working great.:popcorn:

My PPA has been updated too, if you want to install via apt :)

---

### Post by robertklein86 on 2008-08-29
Your script view only date, they don't view time, and they view only "allday" event. Why?

---

### Post by kaivalagi on 2008-08-29
> **robertklein86 said:**
> Your script view only date, they don't view time, and they view only "allday" event. Why?

I am not quite clear as to what you are saying, but it sounds like you only have all day recursive events setup in your calendar?

Can you please explain more thoroughly please.

FYI, all day events do not have an associated time part, and so don't show it.

To prove things work I just ran the following:

```
conkyGoogleCalendar --username=xxxxxx@googlemail.com --password=xxxxxx --daysahead=3 --nowho
```

and got this, a mixed set of all day and specific timed event output (some fictious added on google calendar for the test):

```
Title: Holiday
Start Time: Mon 18/08/08
End Time: Sat 30/08/08

Title: OOH Support Cover
Start Time: Fri 29/08/08
End Time: Sat 30/08/08

Title: test1
Start Time: Fri 29/08/08 9:00:00 pm 
End Time: Fri 29/08/08 10:00:00 pm 
Location: somewhere1
Description: something1

Title: test2
Start Time: Sat 30/08/08 10:30:00 am 
End Time: Sat 30/08/08 11:30:00 am 
Location: somewhere2
Description: something2

Title: OOH Support Cover
Start Time: Sun 31/08/08
End Time: Mon 01/09/08
```

and with the --allevents options the first 5 events are the same, as expected.

---

### Post by kaivalagi on 2008-09-05
[COLOR="DarkOrchid"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I have updated the script with the following:

[LIST]
[*]Refactored code and added better info and error logging
[*]Added regex removal of trailing email address on who list, so "someone@abc.net" becomes "someone"
[*]Added --version option to display the script version and exit
[/LIST]

I have also updated the first post, to reflect the new way to install this script...you'll be glad to know this script is available through my personal package archive :)

The important thing to note now is that the script is called using this in Conky:

```
{execi 1800 conkyGoogleCalendar ...options...}
```

Rather than something like this as before:

```
{execi 1800 python /path/to/file/conkyGoogleCalendar.py ...options...}
```


Have fun :)

---

### Post by Stefanie on 2008-09-06
Installing through synaptic is much easier, thanks. 
I am struggling with what I think is a bug, though. I use --dateformat="%a %d/%m/%y", but only the weekday is printed. I tried a lot of variants and apparently it's not possible to use whitespaces.

---

### Post by kaivalagi on 2008-09-07
[COLOR="Purple"]**[SIZE="4"]CAPTCHA ISSUE[/SIZE]**[/COLOR]

I just had the google calendar function stop working for me with a "***GoogleCalendarEngine Initialisation:Unexpected error:Captcha Required***" error message.

I am not sure why this happened but to fix the problem go here: **[https://www.google.com/accounts/UnlockCaptcha](https://www.google.com/accounts/UnlockCaptcha)**

I've added a mention to the gotchas section in the first post...

---

### Post by kaivalagi on 2008-09-07
> **Stefanie said:**
> Installing through synaptic is much easier, thanks. 
I am struggling with what I think is a bug, though. I use --dateformat="%a %d/%m/%y", but only the weekday is printed. I tried a lot of variants and apparently it's not possible to use whitespaces.

That is strange, I just tested the script with your dateformat option and it seems to work fine, I get this:

```
   Title: test all day event...
   Start Time: Mon 08/09/08
   End Time: Tue 09/09/08
   Who: kaivalagi

   Title: DPA Archive Catchup
   Start Time: Mon 08/09/08 2:00:00 pm 
   End Time: Mon 08/09/08 3:00:00 pm 
   Location: HGP Meeting Room (G-2) - Castle - Capaci...
   Description: Meeting for people not in the know (like...
   Who: robert.farley, michael.neale, james.macl...

   Title: Updated: Daily Review
   Start Time: Mon 08/09/08 3:30:00 pm 
   End Time: Mon 08/09/08 4:00:00 pm 
   Location: HGP Meeting Room (1-3) - Elm Hill - Capa...
   Who: lucy.lawrence, tim.bates, suhel.khan, an...

```

Still not working for you?

---

### Post by Stefanie on 2008-09-07
It still doesn't work: 

```
conkyGoogleCalendar --username=myname@gmail.com --password=mypassword --dateformat="%a %d/%m/%y" --nowho
Title: Dokter
Start Time: ma 
End Time: ma

Title: Judo
Start Time: ma 
End Time: ma 
Location: Sportoase

Title: Judo
Start Time: do 
End Time: do 
Location: Sportoase

Title: Inschrijven CLT
Start Time: za 
End Time: za

Title: Proclamatie tweede zit
Start Time: za 
End Time: za

```

I also tried "%a %R", "%a %d" and so on.

---

### Post by Stefanie on 2008-09-07
I forgot to mention: this problem didn't occur when I used the old version of ConkyGoogleCalendar .

---

### Post by kaivalagi on 2008-09-07
> **Stefanie said:**
> I forgot to mention: this problem didn't occur when I used the old version of ConkyGoogleCalendar .

What happens when you remove the dateformat option?

Can you run the script from the termal too, with the --verbose option set?

[COLOR="Blue"]
Edit: I've attached a test python script to output the date formats on your machine, can you run it and let me know what you get back?

Extract it onto your desktop and run:
```

python ~/Desktop/fmtout.py
```

I got the following output:

```
date format from OS: %d/%m/%y
time format from OS: %l:%M:%S %P %Z
```
[/COLOR]

---

### Post by Stefanie on 2008-09-07
```
python fmtout.py 
date format from OS: %d-%m-%y
time format from OS: 
```

from terminal with verbose option:

```
conkyGoogleCalendar --username=myname@gmail.com --password=mypassword --dateformat="%a %R" --daysahead=8 --limit=4 --nowho --verbose
*** INITIAL OPTIONS:
    username: myname@gmail.com
    password: mypassword
    daysahead: 8
    startdate: None
    enddate: None
    allevents: False
    wordsearch: None
    limit: 4
    template: None
    dateformat: %a
    indent: 0
    nowho: True
    verbose: True
INFO: Initialising google calendar connection...
INFO: Fetching future event data, for the next 8 days...
INFO: Processing output...
Title: dokter
Start Time: ma 
End Time: ma

Title: Judo
Start Time: ma 
End Time: ma 
Location: Sportoase

Title: Judo
Start Time: do 
End Time: do 
Location: Sportoase

Title: Inschrijven CLT
Start Time: za 
End Time: za

```

---

### Post by Stefanie on 2008-09-07
I don't know if this is important but I reconfigured the locales, this is the content of /etc/environment:

```
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"
LC_TIME="nl_BE.UTF-8"
LC_MONETARY="nl_BE.UTF-8"
```

---

### Post by Stefanie on 2008-09-07
I've been trying some things and when I set LC_TIME to "en_GB.UTF-8", it works but it doesn't with nl_BE.UTF-8 or nl_NL.UTF-8. I changed the locale files in /usr/share/i18n/locales (replaced the LC_TIME part in en_GB with the one from nl_BE) but that didn't help.

---

### Post by kaivalagi on 2008-09-07
> **Stefanie said:**
> I've been trying some things and when I set LC_TIME to "en_GB.UTF-8", it works but it doesn't with nl_BE.UTF-8 or nl_NL.UTF-8. I changed the locale files in /usr/share/i18n/locales (replaced the LC_TIME part in en_GB with the one from nl_BE) but that didn't help.

The old version of the script works the same way if no dateformat option is used (I think..depends which old version really :), can you send me the old working version?). What happens when you don't set the --dateformat option, does the output fall back to %d/%m/%y?

To be honest I can't see how things can be broken, but then I don't know enough about locales in Linux for an informed decision. From what I know just formatting a datetime using a %a or %d etc is not something that should be messed up by locales....locales define a default behaviour that's all...(I think)

I don't know how I can really help here? Your locales are setup in such a strange way I wouldn't know where to begin. But then I wouldn't expect them to cause you issues like this anyway...

Maybe you can ask for help further a field? Someone may have come across this issue before now.

---

### Post by Stefanie on 2008-09-08
Before I used an older version of your script, I think there wasn't a --dateformat option yet so I changed some values in your original conkyGoogleCalendar.py script. You find it in attachment. 

If I don't use the --dateformat option now, everything works as expected:
```

 conkyGoogleCalendar --username=myname@gmail.com --password=mypassword --daysahead=8 --limit=4 --nowho
Title: Judo
Start Time: ma 08-09-08 
End Time: ma 08-09-08 
Location: Sportoase

Title: Judo
Start Time: do 11-09-08 
End Time: do 11-09-08 
Location: Sportoase

Title: Inschrijven CLT
Start Time: za 13-09-08 
End Time: za 13-09-08

Title: Proclamatie tweede zit
Start Time: za 13-09-08 
End Time: za 13-09-08

```

If I set all my locales to en_GB, it always works even with the dateformat option. If I set all my locales to nl_BE, it only works without the option. Same goes for your script fmtout.py: it never returns a value for "time format from OS", unless I change the locale from nl_BE to en_GB. 

So I think there's a bug in the dutch locales, or in the way Python retrieves the information (??? I'm no expert at all)

---

### Post by Stefanie on 2008-09-08
Sorry for double posting, but I think I found the solution. The problem occurs with all locales which use a 24hr system instead of AM/PM. In your script you use the "T_FMT_AMPM" variable. In 24hr locales, however, this variable is always empty.  So I think you should use a different variable. I guess it is T_FMT, at least this works for me when I edit /usr/share/conkygooglecalendar/conkyGoogleCalender.py accordingly:

 ```
 # format date based on format string passed
            if dateformat == None:
                self.datetimeformat = "%a "+locale.nl_langinfo(locale.D_FMT)+" "+locale.nl_langinfo(locale.T_FMT_AMPM)
                self.dateonlyformat = "%a "+locale.nl_langinfo(locale.D_FMT)
            elif dateformat == "":
                self.datetimeformat = locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = locale.nl_langinfo(locale.D_FMT) # if no formating but only required to show date we need then revert to default!
            else:
                self.datetimeformat = dateformat+" "+locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = dateformat

```

---

### Post by kaivalagi on 2008-09-08
> **Stefanie said:**
> Sorry for double posting, but I think I found the solution. The problem occurs with all locales which use a 24hr system instead of AM/PM. In your script you use the "T_FMT_AMPM" variable. In 24hr locales, however, this variable is always empty.  So I think you should use a different variable. I guess it is T_FMT, at least this works for me when I edit /usr/share/conkygooglecalendar/conkyGoogleCalender.py accordingly:

 ```
 # format date based on format string passed
            if dateformat == None:
                self.datetimeformat = "%a "+locale.nl_langinfo(locale.D_FMT)+" "+locale.nl_langinfo(locale.T_FMT_AMPM)
                self.dateonlyformat = "%a "+locale.nl_langinfo(locale.D_FMT)
            elif dateformat == "":
                self.datetimeformat = locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = locale.nl_langinfo(locale.D_FMT) # if no formating but only required to show date we need then revert to default!
            else:
                self.datetimeformat = dateformat+" "+locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = dateformat

```

Okay, nicely spotted. I'll make the change tonight when I get back from work.

I think I'll add a --timeformat option too so the user has the ability to change the whole event datetmie output...

I can then put locale based defaults in for both date and time that work for all...like you've described above (i.e. 24 hour clock)

Expect a new version at some point tonight :)

---

### Post by kaivalagi on 2008-09-08
[COLOR="Indigo"]**[SIZE="5"]UPDATE[/SIZE]**[/COLOR]

Stefanie, let me know how you get on with this version *fingers crossed*

I've updated the script, it is available on the first post and through the apt repository.

Changes are:
[LIST]
[*]Changed default time format locale used for output, now 24hr clock based to hopefully support all language locales
[*]Added timeformat option to allow changing the default time formatting of output, this does no support a blank setting
[/LIST]

Have fun

---

### Post by kaivalagi on 2008-09-08
> **Stefanie said:**
> Sorry for double posting, but I think I found the solution. The problem occurs with all locales which use a 24hr system instead of AM/PM. In your script you use the "T_FMT_AMPM" variable. In 24hr locales, however, this variable is always empty.  So I think you should use a different variable. I guess it is T_FMT, at least this works for me when I edit /usr/share/conkygooglecalendar/conkyGoogleCalender.py accordingly:

 ```
 # format date based on format string passed
            if dateformat == None:
                self.datetimeformat = "%a "+locale.nl_langinfo(locale.D_FMT)+" "+locale.nl_langinfo(locale.T_FMT_AMPM)
                self.dateonlyformat = "%a "+locale.nl_langinfo(locale.D_FMT)
            elif dateformat == "":
                self.datetimeformat = locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = locale.nl_langinfo(locale.D_FMT) # if no formating but only required to show date we need then revert to default!
            else:
                self.datetimeformat = dateformat+" "+locale.nl_langinfo(locale.T_FMT)
                self.dateonlyformat = dateformat

```

I have just discovered another issue which may relate to your bug...

For some reason the arguments passed to the shell script which calls the python script (/usr/bin/conkyGoogleCalendar), are messed up when there are spaces in them. so --dateformat="%a %d %b" will be split up into 3 args I think, hence you only see the equivalent to --dateformat=%a

If you call the script in conky using "python /usr/share/conkyGoogleCalendar.py..." all is okay...

I am investigating it, there must be a better way to pass the arguments to the python script from a script file in usr/bin...maybe another very simple python script :)

The reason I didn't reproduce the problem before was that I was running your options in eclipse for debugging and not via the /usr/bin script

Any ideas? How is you knowledge of shell scripting?
[COLOR="Blue"]
Edit: for now edit the /usr/bin/conkyGoogleCalendar file, replacing the $1 $2...$9 with  "$@" (incl quotes), whitespace is then preserved :)[/COLOR]

---

### Post by Stefanie on 2008-09-09
Thanks for all your hard work, it's very nice to see somebody who supports his scripts so well :-)

The new version of the script is indeed much better. 

```
conkyGoogleCalendar --username=myname@gmail.com --password=mypassword --dateformat="%a %R" --daysahead=8 --limit=4 --nowho
Title: Judo
Start Time: do 20:00:00
End Time: do 22:00:00
Location: Sportoase

Title: Inschrijven CLT
Start Time: za 11:00:00
End Time: za 11:30:00

Title: Proclamatie tweede zit
Start Time: za 14:00:00
End Time: za 15:00:00

Title: Geboortefeest Othon
Start Time: zo 10:00:00
End Time: zo 11:00:00

```

It's a bit strange that "%a %R" still gives seconds, this shouldn't be the case. Maybe this is because T_FMT is almost always "%T"? Or does it have to do with the whitespace-issue? Anyway, the problem is solved by adding --timeformat="%R" : 

```
conkyGoogleCalendar --username=myname@gmail.com --password=mypassword --dateformat="%a %R" --timeformat="%R" --daysahead=8 --limit=4 --nowho
Title: Judo
Start Time: do 20:00
End Time: do 22:00
Location: Sportoase

Title: Inschrijven CLT
Start Time: za 11:00
End Time: za 11:30

Title: Proclamatie tweede zit
Start Time: za 14:00
End Time: za 15:00

Title: Feest
Start Time: zo 10:00
End Time: zo 11:00

```

---

### Post by kaivalagi on 2008-09-09
> **Stefanie said:**
> Thanks for all your hard work, it's very nice to see somebody who supports his scripts so well :-)

If I deliver a script for use that doesn't work, what's the point :)

If I didn't care about supporting a script, I wouldn't post it here!

Glad you have found use for it ;)

---

### Post by kaivalagi on 2008-09-25
[COLOR="Purple"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I was waiting for some other updates to be required before releasing a new script with a command line argument fix to allow whitespaces in an option, but none came.

I have updated the first post with the new script and also updated the apt package online...

Unless there are any new requests or bugs found, this script will not be changing :)

---

### Post by Sciophobia on 2008-09-25
Sorry but I didn't see this anywhere.  It seems like it is only checking my personal calendar, is there an option I'm missing to have it check all my other owned calendars or to pick which ones to use?

---

### Post by kaivalagi on 2008-09-26
> **Sciophobia said:**
> Sorry but I didn't see this anywhere.  It seems like it is only checking my personal calendar, is there an option I'm missing to have it check all my other owned calendars or to pick which ones to use?

Nope sorry, I think the gdata functions provided by google only target the main calendar....

I'll do some digging when I get time though, you never know, things might have changed since I last looked into all that...

---

### Post by Sciophobia on 2008-09-26
I don't know Python yet, but it looks like this guy found a way to do it:
[http://code.google.com/p/gcalcli/](http://code.google.com/p/gcalcli/)

If you are feeling ambitious.

Otherwise I will just pipe that to a file or conky directly if possible.

---

### Post by kaivalagi on 2008-09-27
> **Sciophobia said:**
> I don't know Python yet, but it looks like this guy found a way to do it:
[http://code.google.com/p/gcalcli/](http://code.google.com/p/gcalcli/)

If you are feeling ambitious.

Otherwise I will just pipe that to a file or conky directly if possible.

There is promise...use gcalcli for the short term, this is not something I will be tackling in the immediate future...work pressures mean that my free time is a little more precious right now :)

---

### Post by kaivalagi on 2008-10-04
[COLOR="DarkGreen"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script, it is available in the first post and via apt, changes below:

[LIST]
[*]Updated script to remove the whole line from a template based output where no data is available for the required output, this will mean all template output should be on new lines, but enables conky based formatting in the template when using execp or execpi
[*]Updated README
[/LIST]

The reason I changed it's handling of template based output was so that if used in conjunction with execpi/execp in conky, you could format the template output using $color, $font, $goto..., and not have left over rubbish if for example location was not available for an event

Have fun

---

### Post by Stefanie on 2008-10-05
i updated conkyGoogleCalendar today (via the repos) and now it seems like the "--nowho" option stopped working.

```
 conkyGoogleCalendar --username=myusername@gmail.com --password=mypassword --dateformat="%a" --timeformat="%R" --daysahead=8 --limit=2 --nowho
Title: Verjaardag van Tim
Start Time: ma
End Time: di
Who: <who>

Title: Info vergadering
Start Time: ma 16:30
End Time: ma 17:30
Who: <who>


```

i think the problem is line 419
```
output = self.removeLineByString(output,"<who>")
```
if i replace this line with 
```
 
output = output.replace("Who:","") 
output = output.replace("<who>","")
```
(from the previous version of conkyGooglecCalendar.py) everything is fine.

---

### Post by kaivalagi on 2008-10-05
Working for me fine (see attached)...I'll do a bit of digging

---

### Post by Stefanie on 2008-10-06
have you tried using the --nowho option? in your output your "who's" are present.

---

### Post by kaivalagi on 2008-10-06
> **Stefanie said:**
> have you tried using the --nowho option? in your output your "who's" are present.

Sorry, I misread your question...

works okay with a template as the template I have has a newline at the end. Without a template I get the same problem, see attached

To correct it for the short term change this line:

```
template = indent+"Title: <title>\n" + indent + "Start Time: <starttime>\n" + indent + "End Time: <endtime>\n" + indent + "Location: <location>\n" + indent + "Description: <description>\n" + indent + "Who: <who>"
```

to:

```
template = indent+"Title: <title>\n" + indent + "Start Time: <starttime>\n" + indent + "End Time: <endtime>\n" + indent + "Location: <location>\n" + indent + "Description: <description>\n" + indent + "Who: <who>\n"
```

I run it using this in conky:

```
${execpi 10600 conkyGoogleCalendar --nowho --username=???@googlemail.com --password=??? --daysahead=14 --limit=4 --dateformat="%a, %d %b" --timeformat="%H:%M" --template=/home/mark/Scripts/conky/conkyGoogleCalendar.template}
```

and have this template:

```
${color3}Title: ${color1}<title>
${color3}Start Time: ${color1}<starttime>
${color3}End Time: ${color1}<endtime>
${color3}Location: ${color1}<location>
${color3}Description: ${color1}<description>
${color3}Who: ${color1}<who>

```

---

### Post by firecat53 on 2008-10-10
[SOLVED] Nevermind . . . I just changed execi to execpi and increased the buffer size to 2048 and it worked great!

Can't seem to get this functioning correctly . . . it works great from the command line:
```
conkyGoogleCalendar --username=username@comcast.net --password=***** --nowho --template=/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template
```

Gives:
```
${color3}Title: ${color1}Syd - About Me Poster due
${color3}Start Time: ${color1}Thu 10/09/2008
${color3}End Time: ${color1}Fri 10/10/2008

${color3}Title: ${color1}Kids-Bela's
${color3}Start Time: ${color1}Thu 10/09/2008
${color3}End Time: ${color1}Fri 10/10/2008
${color3}Description: ${color1}Kids-Bela's
Kids-Bela's

${color3}Title: ${color1}S
${color3}Start Time: ${color1}Sat 10/11/2008
${color3}End Time: ${color1}Sun 10/12/2008
${color3}Description: ${color1}S
S

```

So that part works great. However, when I use it in the .conkyrc, I get a brief small box in the corner, and then nothing. That instance of conky dies, no error messages, nothing. Any ideas? I'm really baffled!

.conkyrc:
```
background yes
out_to_console no
use_xft yes
xftfont dejavusans:size=8
xftalpha 1.0
update_interval 20 
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 
double_buffer yes
minimum_size 5 5
draw_shades yes
draw_outline no
draw_borders yes
stippled_borders 0
border_margin 10
border_width 2
default_color white
default_shade_color black
default_outline_color white
alignment top_left
gap_x 20
gap_y 20
use_spacer right
no_buffers yes
uppercase no
# colours for Google Calendar
color1 white
# light blue
color2 6892C6
# orange
color3 E77320
# green
color4 78BF39
# red
color5 CC0000
text_buffer_size 512
TEXT
${execi 1800 conkyGoogleCalendar --username=user@comcast.net --password=***** --nowho --template=/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template}


```

Conky works fine otherwise...just fails on this script. Would the @ sign in the username make any difference? We don't have the [email]username@gmail.com[/email] (no gmail account), just the calendar. But, like I said, it works fine on the command line.

Thanks!
Scott

---

### Post by obriente on 2008-10-12
Is there anyway to get this to pull in calendars other than just events from your default calendar?  

For example I keep 3 separate calendars, 1 for personal events and info, 1 for school, and one for work.

any ideas? is this even posible?

---

### Post by obriente on 2008-10-12
Nevermind, i should have looked harder before posing my question... lets hope this changes one day.

---

### Post by kaivalagi on 2008-10-13
[COLOR="Red"][SIZE="6"]**UPDATE**[/SIZE][/COLOR]

I've updated the script to **[SIZE="3"]retrieve all calendar data[/SIZE]** rather than the default calendar, as there was some interest in it.

I've updated the first post and the new apt package is available

All the changes are listed below.

[LIST]
[*]Updated script to work properly without a template, now --nowho option works when no template used
[*]Updated script to bring back event data for ALL calendars available, not just the default one
[*]Added --requestCalendarNames option to pick and choose which calendars event data should be returned, e.g. --requestCalendarNames="cal1;cal2;other cal". If not set all calendar events are returned
[/LIST]

Chimo

---

### Post by Sciophobia on 2008-10-13
:guitar:=D>

---

### Post by Bruce M. on 2008-10-20
**EDIT:** Cancelling this ... I figured it out the problem and have it working.

Yea, works nice!

CHIMO!
Bruce

---

### Post by obriente on 2008-10-21
> **kaivalagi said:**
> 

I've updated the script to **[SIZE="3"]retrieve all calendar data[/SIZE]** rather than the default calendar, as there was some interest in it.


Allow me to just say Woo Hoo!

---

### Post by steveydoteu on 2008-10-24
If my gcal online displays in my timezone, how is one able to tell conky to also use that timezone?

EDIT: Worked it out now, was obvious all along.

---

### Post by Crashmaxx on 2008-10-24
I keep getting this error when I try to run it.
```
ERROR: getAllEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId en.usa', 'reason': 'Bad Request'}

```

I've checked and double checked my username and password and the program seems to get it cause the verbrose output is this.
```

*** INITIAL OPTIONS:
    username: myusername
    password: mypassword
    daysahead: 7
    startdate: None
    enddate: None
    allevents: True
    wordsearch: None
    limit: 0
    template: None
    dateformat: None
    indent: 0
    nowho: False
    verbose: True
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching all event data...
ERROR: getAllEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId en.usa', 'reason': 'Bad Request'}
INFO: Processing output...
No Events...

```

Any idea what's wrong?

---

### Post by Abaddon on 2008-10-24
I use Two colours - grey and white in my Conky script, but the template doesn't seem to be playing the game:

My Template:

```
${color} Name    : ${color white} <title>
${color} Start   : ${color white} <starttime>
${color} End     : ${color white} <endtime>
${color} Location: ${color white} <location>
${color}
```

My .conkyrc line
```
${execi 1800 conkyGoogleCalendar -u secret -p squirrel -F "%H%M" -n -t ~/conkyGoogleCalendar.template}
```

The results are attached.

Help!

---

### Post by Bruce M. on 2008-10-24
> **Abaddon said:**
> I use Two colours - grey and white in my Conky script, but the template doesn't seem to be playing the game:

My .conkyrc line
```
${execi 1800 conkyGoogleCalendar -u secret -p squirrel -F "%H%M" -n -t ~/conkyGoogleCalendar.template}
```

The results are attached.

Help!

```
${**execpi** 1800 conkyGoogleCalendar -u secret -p squirrel -F "%H%M" -n -t ~/conkyGoogleCalendar.template}
```

Try that - ***execpi*** in your line.

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-24
> **Crashmaxx said:**
> I keep getting this error when I try to run it.
```
ERROR: getAllEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId en.usa', 'reason': 'Bad Request'}

```

Any idea what's wrong?

Show us your conky code line calling the calendar.

Bruce

---

### Post by Crashmaxx on 2008-10-24
> **Bruce M. said:**
> Show us your conky code line calling the calendar.

Bruce

```

${color F8DF58}${font StyleBats:size=18}U ${font}${execi 1800 conkyGoogleCalendar -u crashmaxx -p ****** -r "Andrew Stowell;Kappa Delta Rho;York College;US Holidays" -l 10}

```

---

### Post by Bruce M. on 2008-10-24
> **Crashmaxx said:**
> ```

${color F8DF58}${font StyleBats:size=18}U ${font}${execi 1800 conkyGoogleCalendar -u crashmaxx -p ****** -r "Andrew Stowell;Kappa Delta Rho;York College;US Holidays" -l 10}

```

OK, don't quote me here but I think it might be the spaces in the names of the calendars:
```
"Andrew_Stowell;Kappa_Delta_Rho;York_College;US_Holidays"
```

I may be totally out to lunch here, I'm new with the calendar script but that looks like a potential place for an error.

Maybe someone else will know more.
Sorry I couldn't be more help.
Bruce

---

### Post by Crashmaxx on 2008-10-24
> **Bruce M. said:**
> OK, don't quote me here but I think it might be the spaces in the names of the calendars:
```
"Andrew_Stowell;Kappa_Delta_Rho;York_College;US_Holidays"
```

I may be totally out to lunch here, I'm new with the calendar script but that looks like a potential place for an error.

Maybe someone else will know more.
Sorry I couldn't be more help.
Bruce

I got it figured out. I had US Holidays in there, but that is not my calendar, its Google's. That's why it wouldn't work, too bad it didn't give an error that made sense.

---

### Post by kaivalagi on 2008-10-25
> **Crashmaxx said:**
> I got it figured out. I had US Holidays in there, but that is not my calendar, its Google's. That's why it wouldn't work, too bad it didn't give an error that made sense.

The error is what google's gdata api spits out...

I'll try and recreate the problem myself, it might be the content can be returned...with a tweak or two

Might look at it this weekend...

Chimo

[COLOR="Blue"]Edit: I have tried numerous public calendars and they are all fine, can you tell me exactly which public calendar you are using?[/COLOR]

---

### Post by kaivalagi on 2008-10-29
**[COLOR="Purple"][SIZE="5"]UPDATE[/SIZE][/COLOR]**

I've updated the script to require a deliberate new line at the end of a custom template file for blank line separators between event output. This is so that output can have no blank lines if required, therefore reducing the desktop area required.

**Templates may require updating to get a blank space again!**

The first post has been updated, and the apt package is available

Chimo

---

### Post by Bruce M. on 2008-10-29
> **kaivalagi said:**
> **[COLOR="Purple"][SIZE="5"]UPDATE[/SIZE][/COLOR]**

Great news, with all my conkys my desktop space is becoming prime property.

Thatnks kaivalagi, as usual, you do good stuff.

Chimo!
Bruce

---

### Post by shnomin on 2008-11-01
I am getting this error:

ERROR: getFutureEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}


with this line in my conkyrc:

${color F8DF58}${font}${execi 600 conkyGoogleCalendar --username=myusername --password=mypassword --daysahead=28 --limit=10}

what am i doing wrong?

---

### Post by kaivalagi on 2008-11-01
> **shnomin said:**
> I am getting this error:

ERROR: getFutureEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}


with this line in my conkyrc:

${color F8DF58}${font}${execi 600 conkyGoogleCalendar --username=myusername --password=mypassword --daysahead=28 --limit=10}

what am i doing wrong?

Nothing looks wrong.

I think this is the same problem with public calendars as crashmaxx has described above, to fix the issue he removed it from the list of required calendars.

In your case you don't have a list defined, and could setup a list using the -r option, making sure the offending calendar isn't included. The help for this is:

```
  -r TEXT, --requestCalendarNames=TEXT
                        Define a list of calendars to request event data for,
                        calendar names should be separated by semi-colons ";".
                        For example --requestCalendarNames="cal1;cal2;other
                        cal" If not set all calendar data will be returned.
```

I suggest adding calendar names, to the option, one by one until the problem occurs, then you'll know what's causing it.

When you find out please let me know, so I can hopefully reproduce the problem and be able to fix it...

Hope that helps

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
humm

---

### Post by kaivalagi on 2008-11-01
> **francis_ba said:**
> [IMG]http://tinyurl.com/rerunner/[/IMG]
humm

? Same problem when you are running the script?

Any feedback on ways to reproduce would be great, so I can steop through the code and see what's going on exactly...

---

### Post by kaivalagi on 2008-11-02
[COLOR="Green"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've published a new package labelled for Intrepid, starting at version 2.0.

The first post has been updated, and the package is available via apt.

To use the new intrepid "labelled" packages via apt, changes to your sources.list are needed. This:

```
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
deb-src http://ppa.launchpad.net/m-buck/ubuntu hardy main
```

Needs to become this:

```
deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main
deb-src http://ppa.launchpad.net/m-buck/ubuntu intrepid main
```

Currently either hardy or intrepid packages will work with either version of ubuntu.

However going forwards there are no guarantees that packages will continue to work with hardy, development may introduce intrepid specific dependencies. All future revisions will only be available for intrepid.

---

### Post by anxiousdog on 2008-11-02
Seems like I'm having trouble every where tonight! :) 

I'm getting this error:

```
Error: GoogleCalendarEngine Initialisation:Unexpected error:'root'
```

This is my template:

```
${color1}${font Print Bold:size=14}${execi 600 conkyGoogleCalendar --username=name@mydomain.com --password=****** --daysahead=14 --limit=10 --requestCalendarNames="kids"}
```

It is worth noting that 
**1** I'm using Intrepid 
**2** I'm using GoogleApps for my GoogleCalendar
**3** I have the latest version of both Conky and Gcal.

---

### Post by kaivalagi on 2008-11-03
> **anxiousdog said:**
> Seems like I'm having trouble every where tonight! :) 

I'm getting this error:

```
Error: GoogleCalendarEngine Initialisation:Unexpected error:'root'
```

This is my template:

```
${color1}${font Print Bold:size=14}${execi 600 conkyGoogleCalendar --username=name@mydomain.com --password=****** --daysahead=14 --limit=10 --requestCalendarNames="kids"}
```

It is worth noting that 
**1** I'm using Intrepid 
**2** I'm using GoogleApps for my GoogleCalendar
**3** I have the latest version of both Conky and Gcal.

Do you have events displayed ever? Have you got python-gdata installed?

I wonder whether google calendar was down for a short time?

I am not having any initialisation problems...

---

### Post by anxiousdog on 2008-11-03
> **kaivalagi said:**
> Do you have events displayed ever? Have you got python-gdata installed?

I wonder whether google calendar was down for a short time?

I am not having any initialisation problems...

I haven't had events displayed ever. I'm still getting the issue this morning and I'm wondering if it has something to do with either using Google Apps or maybe this issue with [Rhythmbox]("http://ubuntuforums.org/showpost.php?p=6094078&postcount=21")?

Also, I do have the latest python-gdata installed.

---

### Post by kaivalagi on 2008-11-03
> **anxiousdog said:**
> I haven't had events displayed ever. I'm still getting the issue this morning and I'm wondering if it has something to do with either using Google Apps or maybe this issue with [Rhythmbox]("http://ubuntuforums.org/showpost.php?p=6094078&postcount=21")?

I don't think the 2 script issues are related

Could you register a new gmail account and setup a test calendar? I think we ought to find out whether it is a support libraries issue, script issue or a calendar issue.

If you setup an account and PM the login details to me, we can both try using the script locally, and work through the issues that way.

Sound like a plan?

---

### Post by anxiousdog on 2008-11-03
> **kaivalagi said:**
> I don't think the 2 script issues are related

Could you register a new gmail account and setup a test calendar? I think we ought to find out whether it is a support libraries issue, script issue or a calendar issue.

If you setup an account and PM the login details to me, we can both try using the script locally, and work through the issues that way.

Sound like a plan?

Sounds like a plan. :) I'll be out this morning so I'll PM you before I leave. :)

---

### Post by anxiousdog on 2008-11-04
Just wondering if anyone has got this working with a google apps account?

---

### Post by megagurius on 2008-11-05
Has anyone gotten the script to work with unicode characters in event names? I get the script to work perfectly for all my needs, except when I try to add my "birthday reminder" calendar and there are event names with unicode characters.

I would love a fix for this, since "your name crashed conky" is not a valid reason for forgetting your sisters birthday.

Olle

---

### Post by kaivalagi on 2008-11-05
> **megagurius said:**
> Has anyone gotten the script to work with unicode characters in event names? I get the script to work perfectly for all my needs, except when I try to add my "birthday reminder" calendar and there are event names with unicode characters.

I would love a fix for this, since "your name crashed conky" is not a valid reason for forgetting your sisters birthday.

Olle

Can't have that!

As far as I know, the only thing you need to do to get conky working with extended character sets is to add the following above the TEXT section:

```

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
```

Failing that, can you edit the script and let me know if it fixes the issue?

If you installed via apt or the deb file, then to edit the script in gnome run this:

```
gksudo gedit /usr/share/conkygooglecalendar/conkyGoogleCalendar.py
```

Then change the line:

```
print output
```

to this:

```
print output.encode("utf-8")
```


If this works then let me know :)

---

### Post by megagurius on 2008-11-06
> 
...

Failing that, can you edit the script and let me know if it fixes the issue?

Then change the line:

```
print output
```

to this:

```
print output.encode("utf-8")
```


If this works then let me know 


It worked perfectly! Thanks! Even for characters like &#24618;&#29539;&#26144;&#30011;

Now I just have to figure out a way to make conky fallback to a font that includes japanese characters when needed.

Olle

---

### Post by kaivalagi on 2008-11-06
> **megagurius said:**
> It worked perfectly! Thanks! Even for characters like &#24618;&#29539;&#26144;&#30011;

Now I just have to figure out a way to make conky fallback to a font that includes japanese characters when needed.

Olle

I'll make the utf encoding change in the next release

On the font issue, just make sure you use a font with support of the unicode characters you need output for...

---

### Post by sssimon on 2008-11-10
I get the following error:

$ conkyGoogleCalendar -u ... -p ... 
Title: Tasks for Monday (Nov 10)
Start Time: Mon 11/10/2008
End Time: Tue 11/11/2008
Who: o78s3eqe3ov403cpuav2bje5ja9j1tp2

**ERROR: getOutputText:Unexpected error:'latin-1' codec can't encode character u'\u0142' in position 42: ordinal not in range(256)**

Any ideas?

---

### Post by kaivalagi on 2008-11-10
> **sssimon said:**
> I get the following error:

$ conkyGoogleCalendar -u ... -p ... 
Title: Tasks for Monday (Nov 10)
Start Time: Mon 11/10/2008
End Time: Tue 11/11/2008
Who: o78s3eqe3ov403cpuav2bje5ja9j1tp2

**ERROR: getOutputText:Unexpected error:'latin-1' codec can't encode character u'\u0142' in position 42: ordinal not in range(256)**

Any ideas?

See my previous post :)

---

### Post by hachel on 2008-11-10
my script has problems displaying umlauts, it just doesn't display anything at all. i ran it through console, but forgot what it said. Something with the likes of utf or unicode or something

---

### Post by Eemeez on 2008-11-10
> **megagurius said:**
> Has anyone gotten the script to work with unicode characters in event names? I get the script to work perfectly for all my needs, except when I try to add my "birthday reminder" calendar and there are event names with unicode characters.

I would love a fix for this, since "your name crashed conky" is not a valid reason for forgetting your sisters birthday.

Olle

I got all my conky programs to display unicode characters by adding ```
| iconv -f UTF8 -t ISO885915
``` on the end .. so for example
```
${execi 1800 program --commands | iconv -f UTF8 -t ISO885915}
```

---

### Post by kaivalagi on 2008-11-10
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Added utf-8 encoding to output
[*]Added --errorlog and --infolog options to log data to a file
[*]Refactored and tidied up
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by kaivalagi on 2008-11-19
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Now loading the template file in unicode mode to allow for the extended character set
[*][SIZE="4"]**[COLOR="Red"]Changed option tags from <...> to [...][/COLOR]**[/SIZE], so <eta> now needs to be [eta] in the template to work
[*]Updated example template and README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by steveydoteu on 2008-11-20
Aha, that would be why mine started to display the template variables rather than the events!

---

### Post by weezerisrock on 2008-11-20
> **steveydoteu said:**
> Aha, that would be why mine started to display the template variables rather than the events!

Same thing here! I was wondering what had changed!  lol:)

---

### Post by Bruce M. on 2008-11-20
> **steveydoteu said:**
> Aha, that would be why mine started to display the template variables rather than the events!

> **weezerisrock said:**
> Same thing here! I was wondering what had changed!  lol:)

hehehehe I cheated, I read these two posts before I got the update so I was ready for it.

<Have a> [nice day] :lolflag:
Bruce

---

### Post by sssimon on 2008-11-27
In the latest version, I get the following error:
ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)

I think this did not happen with the previous version.

---

### Post by Bruce M. on 2008-11-27
> **sssimon said:**
> In the latest version, I get the following error:
ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)

I think this did not happen with the previous version.

Not sure but it looks like an issue with the font.
What font are you using?
Try changing it and see what happens.

Have a nice day.
Bruce

---

### Post by kaivalagi on 2008-11-27
> **sssimon said:**
> In the latest version, I get the following error:
ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)

I think this did not happen with the previous version.

What locale is you using? Can you post your template?

---

### Post by joakim2 on 2008-11-27
I'm getting stuck at the following error:

INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:'root'
INFO: Fetching future event data, for the next 2 days...
INFO: Processing output...

I ran it like this:

conkyGoogleCalendar -v -u [email]jryden@mydomain.com[/email] -p secret -d 2

---

### Post by kaivalagi on 2008-11-28
> **joakim2 said:**
> I'm getting stuck at the following error:

INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:'root'
INFO: Fetching future event data, for the next 2 days...
INFO: Processing output...

I ran it like this:

conkyGoogleCalendar -v -u [email]jryden@mydomain.com[/email] -p secret -d 2

You using a google app account by any chance?

Anxiousdog has the same issue, not sure whether she got it sorted or not...

Her post: [http://ubuntuforums.org/showthread.php?p=6091592#post6091592](http://ubuntuforums.org/showthread.php?p=6091592#post6091592)

---

### Post by sssimon on 2008-11-28
> **kaivalagi said:**
> What locale is you using? Can you post your template?

$ cat ~/.conkyGoogleCalendar.template
[starttime] [title]

$ locale
LANG=en_US.iso-8859-1
LC_CTYPE="en_US.iso-8859-1"
LC_NUMERIC="en_US.iso-8859-1"
LC_TIME="en_US.iso-8859-1"
LC_COLLATE="en_US.iso-8859-1"
LC_MONETARY="en_US.iso-8859-1"
LC_MESSAGES="en_US.iso-8859-1"
LC_PAPER=en_GB.UTF-8
LC_NAME="en_US.iso-8859-1"
LC_ADDRESS="en_US.iso-8859-1"
LC_TELEPHONE="en_US.iso-8859-1"
LC_MEASUREMENT="en_US.iso-8859-1"
LC_IDENTIFICATION="en_US.iso-8859-1"
LC_ALL=

The character that is generating the error belongs to ISO-8859-2. Should I change my locale?

I get the error message when running gnome-terminal, the encoding is set to either UTF-8 or ISO-8859-2. So to answer Bruce, the font is the system fixed font (Ubuntu Intrepid).

---

### Post by kaivalagi on 2008-11-28
> **sssimon said:**
> $ cat ~/.conkyGoogleCalendar.template
[starttime] [title]

$ locale
LANG=en_US.iso-8859-1
LC_CTYPE="en_US.iso-8859-1"
LC_NUMERIC="en_US.iso-8859-1"
LC_TIME="en_US.iso-8859-1"
LC_COLLATE="en_US.iso-8859-1"
LC_MONETARY="en_US.iso-8859-1"
LC_MESSAGES="en_US.iso-8859-1"
LC_PAPER=en_GB.UTF-8
LC_NAME="en_US.iso-8859-1"
LC_ADDRESS="en_US.iso-8859-1"
LC_TELEPHONE="en_US.iso-8859-1"
LC_MEASUREMENT="en_US.iso-8859-1"
LC_IDENTIFICATION="en_US.iso-8859-1"
LC_ALL=

The character that is generating the error belongs to ISO-8859-2. Should I change my locale?

I get the error message when running gnome-terminal, the encoding is set to either UTF-8 or ISO-8859-2. So to answer Bruce, the font is the system fixed font (Ubuntu Intrepid).

The script works with utf-8, for unicode. You could try messing with your locales...to be honest though my knowledge on this is limited.

---

### Post by Bruce M. on 2008-11-28
> **kaivalagi said:**
> The script works with utf-8, for unicode. You could try messing with your locales...to be honest though my knowledge on this is limited.

Yes, try to get it to look something like this:

```
bruloo@bruloo:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
bruloo@bruloo:~$
```

CHIMO!
Bruce

---

### Post by kaivalagi on 2008-11-28
Like your new logo Bruce, you're definitely sticking with xfce then!

---

### Post by Bruce M. on 2008-11-28
> **kaivalagi said:**
> Like your new logo Bruce, you're definitely sticking with xfce then!

Yea, I really like it. It's fast, it doesn't use Nautilus with all it's "ties" to the system. And as I just found out last week it can even run compiz if I want it to. Not that I want it to, I just like the speed of the thing.  :)

I'd pop FluxBox or OpenBox in here but my wife would kill me as she likes icons and panels and we do share the computer.  :D


Chimo!
Bruce

---

### Post by joakim2 on 2008-11-28
> **kaivalagi said:**
> You using a google app account by any chance?

Anxiousdog has the same issue, not sure whether she got it sorted or not...

Her post: [http://ubuntuforums.org/showthread.php?p=6091592#post6091592](http://ubuntuforums.org/showthread.php?p=6091592#post6091592)

Yes sir - using Google Apps here

---

### Post by kaivalagi on 2008-11-28
> **joakim2 said:**
> Yes sir - using Google Apps here

Well, I can't explain why, but with a google apps based account my script can't access calendar info...

Haven't got to the bottom of the problem...maybe you can help?

Are there any defaults that can put in extra protection on your account which may explain this?

Can you possibly ask google what might cause this issue for you?

The script uses the gdata api to access calendar info....feel free to send them the py file from the install if that will help...

Sorry I can't be of more right now, I am stumped without a google apps account setup

---

### Post by StrangeFreedom on 2008-11-29
There is an extra owner type called 'root' for calenders shared with an entire domain and/or for the adminuser (not sure).

So defining an extra type could be the solution. Maybe better nog to use this script as a domainadmin as it uses plaintext password!

---

### Post by kaivalagi on 2008-11-30
> **StrangeFreedom said:**
> There is an extra owner type called 'root' for calenders shared with an entire domain and/or for the adminuser (not sure).

So defining an extra type could be the solution. Maybe better nog to use this script as a domainadmin as it uses plaintext password!

Thanks for the heads up....not sure on what I can do within the script.

I would expect that if the username and password used with the script is for a google app domain user, then it should work as expected....? again I think this is something that google should address with the gdata api and google apps framework

---

### Post by super.rad on 2008-11-30
This isn't working for me, when conky starts the calender section is empty and if i start it from a terminal i get the following
```
File "/home/fedora/Scripts/conkyGoogleCalendar.py", line 46, in <module>
    import socket, gdata.calendar.service, gdata.service, gdata.calendar
ImportError: No module named gdata.calendar.service
```
This is my .conkyrc
```
${execi 10600 python /home/fedora/Scripts/conkyGoogleCalendar.py --username=*******@googlemail.com --password=****** --daysahead=14 --limit=4 --indent=2}
```
Obviously in my .conkyrc it has my username and password instead of *****

---

### Post by kaivalagi on 2008-11-30
> **super.rad said:**
> This isn't working for me, when conky starts the calender section is empty and if i start it from a terminal i get the following
```
File "/home/fedora/Scripts/conkyGoogleCalendar.py", line 46, in <module>
    import socket, gdata.calendar.service, gdata.service, gdata.calendar
ImportError: No module named gdata.calendar.service
```
This is my .conkyrc
```
${execi 10600 python /home/fedora/Scripts/conkyGoogleCalendar.py --username=*******@googlemail.com --password=****** --daysahead=14 --limit=4 --indent=2}
```
Obviously in my .conkyrc it has my username and password instead of *****

You need to install the gdata api...as you are not using the package and it wont install automatically...

You can get it from here: [http://code.google.com/p/gdata-python-client/downloads/list](http://code.google.com/p/gdata-python-client/downloads/list)

The chances are though that your own distro has the python gdata api in it's repo's...

---

### Post by super.rad on 2008-11-30
I'm using fedora so couldnt install the package. Installed the gdata api and is working now.
Thanks

---

### Post by steveydoteu on 2008-11-30
I am having some issues regarding alignment. I would like it all aligned to the right, but using the following code:

```
$alignr${color8}${execi 600 conkyGoogleCalendar  --username=removed --password=removed --template=/home/steve/conky/cal.template --dateformat="%A" --timeformat="%H:%M" --daysahead=14 --limit=2}
```

I get a result such as that of the attached image.

---

### Post by kaivalagi on 2008-12-01
> **steveydoteu said:**
> I am having some issues regarding alignment. I would like it all aligned to the right, but using the following code:

```
$alignr${color8}${execi 600 conkyGoogleCalendar  --username=removed --password=removed --template=/home/steve/conky/cal.template --dateformat="%A" --timeformat="%H:%M" --daysahead=14 --limit=2}
```

I get a result such as that of the attached image.

Edit your template to have more {alignr} or {goto} statements for ALL the lines that are spat out :)

You'll need to use the execpi option instead...then your template can have alignr/goto/font/color options added

---

### Post by steveydoteu on 2008-12-01
> **kaivalagi said:**
> Edit your template to have more {alignr} or {goto} statements for ALL the lines that are spat out :)

You'll need to use the execpi option instead...then your template can have alignr/goto/font/color options added

Cheers, while we are here, is it possible to remove the gap between items?

---

### Post by kaivalagi on 2008-12-01
> **steveydoteu said:**
> Cheers, while we are here, is it possible to remove the gap between items?

Yep, should be. Make sure there is no carriage return at the last line in a custom template, events should "butt" up against each other then

---

### Post by megagurius on 2008-12-01
The problem with unicode characters returned with the latest version. However, it was easy to fix. Just change the line

```
return output.encode("utf-8")
```

to just

```
return output
```

and it works just fine.

Olle

---

### Post by kaivalagi on 2008-12-01
> **megagurius said:**
> The problem with unicode characters returned with the latest version. However, it was easy to fix. Just change the line

```
return output.encode("utf-8")
```

to just

```
return output
```

and it works just fine.

Olle

The reason I added the unicode method was to handle the output of unicode characters. UTF-8 is widely supported, and so shouldn't be a problem....in theory. utf-8 is also used when reading from the template file etc...

Unless obscure encoding is being used it should be fine, surely?

What will happen if unicode characters are present in the output and no encode method is used?

Am I misunderstanding something here?

---

### Post by megagurius on 2008-12-01
Ok, maybe I wasn't clear. I don't remove all instances of .encode("utf-8"), just the one after return output. I keep the one at the end, at print output.encode("utf-8").

If I keep the first instance the script crashes as soon as an event has utf characters in it.

Please don't ask me why, I know very little python. I just randomly changed stuff that seem ta have something to do with enconding and it happened to work.

Olle

---

### Post by steveydoteu on 2008-12-01
Seems a little odd considering it works for everyone else without having to edit the core.

---

### Post by kaivalagi on 2008-12-02
> **megagurius said:**
> Ok, maybe I wasn't clear. I don't remove all instances of .encode("utf-8"), just the one after return output. I keep the one at the end, at print output.encode("utf-8").

If I keep the first instance the script crashes as soon as an event has utf characters in it.

Please don't ask me why, I know very little python. I just randomly changed stuff that seem ta have something to do with enconding and it happened to work.

Olle

Okay, thanks for painting the picture for me, I'll investigate soon...

Line 389...

That is bizarre!

---

### Post by anxiousdog on 2008-12-07
> **joakim2 said:**
> Yes sir - using Google Apps here


I never did get it to work with Google Apps... If I had a buck for every problem Google Apps causes I'd be able to by a new lens for my camera. :)

---

### Post by kaivalagi on 2008-12-07
> **anxiousdog said:**
> I never did get it to work with Google Apps... If I had a buck for every problem Google Apps causes I'd be able to by a new lens for my camera. :)

I hear you! The lens would be one of those nice L series ones too ;)

---

### Post by sssimon on 2008-12-09
I was getting the message "ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)". 

kaivalagi and Bruce M. said I should change my locale. I couldn't find the time for this, but I did what megagurius suggested and I set "override_utf8_locale yes" in .conkyrc and now it works again :-)

---

### Post by kaivalagi on 2008-12-09
> **sssimon said:**
> I was getting the message "ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128)". 

kaivalagi and Bruce M. said I should change my locale. I couldn't find the time for this, but I did what megagurius suggested and I set "override_utf8_locale yes" in .conkyrc and now it works again :-)

Thanks for the heads up, I've added details to the gotchas section in the first post...

---

### Post by sssimon on 2008-12-09
> **kaivalagi said:**
> Thanks for the heads up, I've added details to the gotchas section in the first post...

I looked into the gotchas section and in fact I didn't just change .conkyrc, but also your python script, like megagurius, by editing "return output.encode("utf-8")" to "return output".

---

### Post by kaivalagi on 2008-12-09
> **sssimon said:**
> I looked into the gotchas section and in fact I didn't just change .conkyrc, but also your python script, like megagurius, by editing "return output.encode("utf-8")" to "return output".

Looks like I'm meeting you half way for now, I'll look into the script later on...still got other work to get through...

Glad you got it working anyway

---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Red"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Red"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by kaivalagi on 2009-02-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Removed .encode("utf-8") from internal return to fix unicode output
[/LIST]

Changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.03_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.03_source.changes)


The first post has been updated and the apt package should be available soon

Chimo

---

### Post by Technoviking on 2009-02-11
Geeting the following error

ERROR: getFutureEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId en.usa', 'reason': 'Bad Request'}
No Events...

${execi 600 conkyGoogleCalendar --username=******** --password=******** --daysahead=7 --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template}

username and password are correct.

---

### Post by kaivalagi on 2009-02-12
> **Technoviking said:**
> Geeting the following error

ERROR: getFutureEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId en.usa', 'reason': 'Bad Request'}
No Events...

${execi 600 conkyGoogleCalendar --username=******** --password=******** --daysahead=7 --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template}

username and password are correct.

I think this error will be caused because of a public calendar which you've added...I haven't got to the bottom of the problem yet though.

Try limiting the calendars used by the script using this option:

```
  -r TEXT, --requestCalendarNames=TEXT
                        Define a list of calendars to request event data for,
                        calendar names should be separated by semi-colons ";".
                        For example --requestCalendarNames="cal1;cal2;other
                        cal" If not set all calendar data will be returned.

```

That should get it working again...if you can tell me the about the offending calendar and where I can find it so I can reproduce the problem I'd be grateful.

Hope that helps

---

### Post by eben on 2009-02-13
your solution for the "no events" problem did the trick for me, thanks. but i don't really want to see my google password in the conkyrc for security reasons. has anyone a solution for this?

---

### Post by kaivalagi on 2009-02-13
> **eben said:**
> your solution for the "no events" problem did the trick for me, thanks. but i don't really want to see my google password in the conkyrc for security reasons. has anyone a solution for this?

Nope sorry, just put your conkyrc in a folder which only your login has access to....simple, e.g. ~/ :)

---

### Post by eben on 2009-02-16
yes, i suppose you are right ...

---

### Post by chochem on 2009-02-18
I'm trying to run the program using the example configuration with my own account name and password subsituted for the example ones. However, I keep getting the following error:

```
Conky: desktop window (77) is root window
Conky: window type - override
Conky: drawing to created window (0x400001)
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Conky: drawing to double buffer
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:[Errno 111] Connection refused
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:[Errno 111] Connection refused

```

As I said, I haven't changed anything apart from the account (yadayada@gmail.com) and password and the reference to the template file which I've copied to a folder under $HOME.

Any suggestions?

---

### Post by kaivalagi on 2009-02-18
> **chochem said:**
> I'm trying to run the program using the example configuration with my own account name and password subsituted for the example ones. However, I keep getting the following error:

```
Conky: desktop window (77) is root window
Conky: window type - override
Conky: drawing to created window (0x400001)
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Conky: drawing to double buffer
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:[Errno 111] Connection refused
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:[Errno 111] Connection refused

```

As I said, I haven't changed anything apart from the account (yadayada@gmail.com) and password and the reference to the template file which I've copied to a folder under $HOME.

Any suggestions?

Did you have any issues on install? Is the python-gdata package on your system?

At first glance it looks like google is down for you, but I doubt that.

The username should include the gmail.com or googlemail.com on the end....

Can't think of what could be causing the issue other than this....

Can you run the same conkyGoogleCalendar command in the terminal, and see what you get there?

---

### Post by chochem on 2009-02-19
I think I got it: I had set the export "HTTP_PROXY=127.0.0.1:8118" variable in a global config file and apparently a) this was being used by the connection and b) port 8118 (privoxy) was being advertised as open. Reset the variable and all is well. Sorry for the confusion.

---

### Post by kaivalagi on 2009-02-19
> **chochem said:**
> I think I got it: I had set the export "HTTP_PROXY=127.0.0.1:8118" variable in a global config file and apparently a) this was being used by the connection and b) port 8118 (privoxy) was being advertised as open. Reset the variable and all is well. Sorry for the confusion.

No worries, I know to look out for that situation now :)

---

### Post by cmorse on 2009-03-10
I really like this script, but is there any way to use the daysahead parameter but have it only print out events for that date, not everything from today until then?  I would like to print events for today, tomorrow and the next day, but put them in separate sections of my conky file and I can't figure out how to do that with the current options (short of hard coding a specific date).  thanks - great work BTW...

---

### Post by kaivalagi on 2009-03-10
> **cmorse said:**
> I really like this script, but is there any way to use the daysahead parameter but have it only print out events for that date, not everything from today until then?  I would like to print events for today, tomorrow and the next day, but put them in separate sections of my conky file and I can't figure out how to do that with the current options (short of hard coding a specific date).  thanks - great work BTW...

I am sure you can still use the start and end date options but construct the dates automatically...

To do this you would want a new script that figures out the dates you need based on todays date, then uses those in calls to the conkyForecast script...

I'll have a look when I get home and onto Linux, I am at work and not infront of a linux PC right now

**===== BEGINNING OF "A" SOLUTION ====================================**

I got a python script which wraps the conkyGoogleCalendar script working. It's not pretty, and you'll need to make a new version of it for each day chunk you want seperately.

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-
from datetime import date, timedelta
import subprocess

STARTDAY = 3 # startday of 0 is today, 1 is tomorrow etc
USERNAME = "???@googlemail.com"
PASSWORD = "???"

startDate = date.today() + timedelta(days=STARTDAY)
endDate = startDate + timedelta(days=1)
subprocess.Popen("conkyGoogleCalendar -u "+USERNAME+" -p "+PASSWORD+" -s "+startDate.strftime("%F")+" -e "+endDate.strftime("%F"),shell=True)[/PHP]

It's fairly self explainatory, you'll need to set values for STARTDAY, USERNAME and PASSWORD. If you want more options added to the calendar script call then the last line needs modifying further...

If you create one script for each day period you want conky output for, you'll get what you need. For an example call I have assumed the script is named getCalStartDay3.py because it gets the events for 3 days ahead, for this you would call it like so:

```
${execi 1800 python /path/to/script/getCalStartDay3.py}
```

I've attached the script too :)

Hope that helps

---

### Post by cmorse on 2009-03-11
> **kaivalagi said:**
> 
I got a python script which wraps the conkyGoogleCalendar script working. It's not pretty, and you'll need to make a new version of it for each day chunk you want seperately.

Hope that helps

That works fine, thank you very much.  I've done very simple bash scripting, plus PHP but haven't ventured into python.  Looking at your example its quite straightforward, but it would have taken me quite a while to wrangle that out on my own..

thanks again..

---

### Post by kaivalagi on 2009-03-11
> **cmorse said:**
> That works fine, thank you very much.  I've done very simple bash scripting, plus PHP but haven't ventured into python.  Looking at your example its quite straightforward, but it would have taken me quite a while to wrangle that out on my own..

thanks again..

No problem

I did try using the shell initially but couldn't figure out a way to add days on to today's date properly...

Python is a piece of cake for simple scripts like this, I'd suggest using it for most things that require data manipulation

---

### Post by Technoviking on 2009-03-23
I'm testing things in Jaunty, most things are working well but I get the following error with the googlecaendar script in Jaunty.
```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
```
I'm guessing it is a Python 2.6 issue, but thought you would like to know.

Here is my line from my .conkyrc.
```
${execi 600 conkyGoogleCalendar --username=username@gmail.com --password=password -r "Calendar" --daysahead=7 --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template}
```

T-V

---

### Post by kaivalagi on 2009-03-24
> **Technoviking said:**
> I'm testing things in Jaunty, most things are working well but I get the following error with the googlecaendar script in Jaunty.
```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
```
I'm guessing it is a Python 2.6 issue, but thought you would like to know.

Here is my line from my .conkyrc.
```
${execi 600 conkyGoogleCalendar --username=username@gmail.com --password=password -r "Calendar" --daysahead=7 --limit=3 --nowho --template=/home/dbasinge/conky/conkyGoogleCalendar.template}
```

T-V

Thanks for the heads up, I think that issue relates specifically with the gdata package in Jaunty...I would hope that the gdata package will get updated to work 100% with python 2.6 before the final release of 9.04

---

### Post by lavarock on 2009-04-02
I got this error when I try to run conkyGoogleCalendar:
```
# conkyGoogleCalendar
  File "/usr/bin/python", line 1
SyntaxError: Non-ASCII character '\x80' in file /usr/bin/python on line 2, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

I am running Python 2.5.2. Any help would be appreciated.

---

### Post by kaivalagi on 2009-04-02
> **lavarock said:**
> I got this error when I try to run conkyGoogleCalendar:
```
# conkyGoogleCalendar
  File "/usr/bin/python", line 1
SyntaxError: Non-ASCII character '\x80' in file /usr/bin/python on line 2, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

Strange, can you make sure the conkyGoogleCalendar bin script is correct, it can be found here:

```
cat /usr/bin/conkyGoogleCalendar
```

And it should look like this:

```
#!/bin/sh
cd /usr/share/conkygooglecalendar/
$PYTHONPATH /usr/bin/python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py "$@"
```

What version of Ubuntu are you running and how did you install the script?

Edit: looks like python is messed up...reinstall "python" through synaptic

---

### Post by lavarock on 2009-04-03
Thanks for the help, it turns out that I have multiple versions of python installed:
```
echo $PYTHONPATH 
/some/other/path/to/python:/usr/lib/python2.5:/usr/lib/python2.5/site-packages

```
so I did
```
#export PYTHONPATH=/usr/bin/python2.5
```
and I got that error, (I also tried /usr/lib/python2.5 or /usr/lib/python2.5/site-packages, none of these work).  Now the question is, is there anyway of running this with multiple versions of python?

---

### Post by kaivalagi on 2009-04-03
> **lavarock said:**
> Thanks for the help, it turns out that I have multiple versions of python installed:
```
echo $PYTHONPATH 
/some/other/path/to/python:/usr/lib/python2.5:/usr/lib/python2.5/site-packages

```
so I did
```
#export PYTHONPATH=/usr/bin/python2.5
```
and I got that error, (I also tried /usr/lib/python2.5 or /usr/lib/python2.5/site-packages, none of these work).  Now the question is, is there anyway of running this with multiple versions of python?

try changing the conkyGoogleCalendar script in /usr/bin to this:

```
#!/bin/sh
cd /usr/share/conkygooglecalendar/
/usr/bin/python2.5 /usr/share/conkygooglecalendar/conkyGoogleCalendar.py "$@"
```

That should hopefully just stick with python 2.5 and all should work...*fingers crossed*

Never come across this issue before, maybe I need to restructure my scripts to cope and have the main script itself in the /usr/bin folder.

If it doesn't work let me know what package setup etc you have so I can try to reproduce the situation

Cheers

---

### Post by lavarock on 2009-04-03
I changed that line, this error was produced:

```
# cat /usr/bin/conkyGoogleCalendar 
#! /bin/sh
cd /usr/share/conkygooglecalendar/
/usr/bin/python2.5 /usr/share/conkygooglecalendar/conkyGoogleCalendar.py "$@"

# conkyGoogleCalendar 
Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 643, in <module>
    main()
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 618, in main
    self.logError("A username and/or password was not given!")
NameError: global name 'self' is not defined

```

I am not sure what do you mean by package setup, but this is what I have for python:
```
#sudo aptitude show python2.5
Package: python2.5
State: installed
Automatically installed: no
Version: 2.5.2-11.1ubuntu1
Priority: important
Section: python
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 10.5M
Depends: python2.5-minimal (= 2.5.2-11.1ubuntu1), mime-support, libbz2-1.0, libc6 (>= 2.7),
         libdb4.6, libncursesw5 (>= 5.6+20071006-3), libreadline5 (>= 5.2), libsqlite3-0 (>=
         3.5.9), libssl0.9.8 (>= 0.9.8f-5)
Suggests: python2.5-doc, python-profiler
Conflicts: idle-python2.5 (< 2.4.3+2.5b2-2), python-central (< 0.5.9), python-tk (< 2.4.3-2)
Replaces: idle-python2.5 (< 2.4.3+2.5b2-2), python-tk (< 2.4.3-2), python2.5-dev (< 2.5.1),
          python2.5-minimal (< 2.5)
Provides: python2.5-celementtree, python2.5-cjkcodecs, python2.5-ctypes,
          python2.5-elementtree, python2.5-plistlib, python2.5-wsgiref
Description: An interactive high-level object-oriented language (version 2.5)
 Version 2.5 of the high-level, interactive object oriented language, includes an extensive
 class library with lots of goodies for network programming, system administration, sounds
 and graphics.
Homepage: http://python.org/

```

Thanks again for helping.

---

### Post by kaivalagi on 2009-04-03
> **lavarock said:**
> I changed that line, this error was produced:

Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 643, in <module>
    main()
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 618, in main
    **self.logError("A username and/or password was not given!")**
NameError: global name 'self' is not defined
[/CODE]


Well, you have gotten around the problem with the script running!

There is now an error when logging an error :) but it does tell you what is wrong...see the text in bold above.

I think you are now at the point of needing to understand how to use the script properly.... There is an example conkyrc and template in /usr/share/conkygooglecalendar/example which will get you started. As stated in the README.txt attachment in the first post of this thread you can run the example by running this (after editing the conkyrc to include your user/password for google):

```
conky -c /usr/share/conkygooglecalendar/example/conkyrc &
```

And in looking at the conkyrc you will see that a typical use of the command (without templates) would be like this (with your user/password for google):

```
conkyGoogleCalendar --username=username@googlemail.com --password=password --daysahead=28 --limit=10
```

> **lavarock said:**
> 
I am not sure what do you mean by package information, but this is what I have for python:
```
#sudo aptitude show python2.5
Package: python2.5
State: installed
Automatically installed: no
Version: 2.5.2-11.1ubuntu1
Priority: important
Section: python
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 10.5M
Depends: python2.5-minimal (= 2.5.2-11.1ubuntu1), mime-support, libbz2-1.0, libc6 (>= 2.7),
         libdb4.6, libncursesw5 (>= 5.6+20071006-3), libreadline5 (>= 5.2), libsqlite3-0 (>=
         3.5.9), libssl0.9.8 (>= 0.9.8f-5)
Suggests: python2.5-doc, python-profiler
Conflicts: idle-python2.5 (< 2.4.3+2.5b2-2), python-central (< 0.5.9), python-tk (< 2.4.3-2)
Replaces: idle-python2.5 (< 2.4.3+2.5b2-2), python-tk (< 2.4.3-2), python2.5-dev (< 2.5.1),
          python2.5-minimal (< 2.5)
Provides: python2.5-celementtree, python2.5-cjkcodecs, python2.5-ctypes,
          python2.5-elementtree, python2.5-plistlib, python2.5-wsgiref
Description: An interactive high-level object-oriented language (version 2.5)
 Version 2.5 of the high-level, interactive object oriented language, includes an extensive
 class library with lots of goodies for network programming, system administration, sounds
 and graphics.
Homepage: http://python.org/

```



What I mean is what python packages have you got installed, you obviously have 2.5 but what else do you have?

Can you run the following too please and post back the info:

```
ls -al /usr/bin/python
```

you should get something like this:
```

lrwxrwxrwx 1 root root 9 2008-10-31 17:08 /usr/bin/python -> python2.5
```

which indicates python 2.5 will be used for all default python processing...

---

### Post by lavarock on 2009-04-03
> **kaivalagi said:**
> Well, you have gotten around the problem with the script running!
Oh! I see, I thought that was still a setup error with the script.

> **kaivalagi said:**
> 
Can you run the following too please and post back the info:

```
ls -al /usr/bin/python
```

you should get something like this:
```

lrwxrwxrwx 1 root root 9 2008-10-31 17:08 /usr/bin/python -> python2.5
```

which indicates python 2.5 will be used for all default python processing...
That's in fact what I have, thanks again for fixing this for me :-)

---

### Post by mockdeep on 2009-04-13
I'm having a problem getting it to use the proper date:

```
$conkyGoogleCalendar -u superman -p Kryptonite -a -r "Super Man" --template=/usr/share/conkygooglecalendar/conkyGoogleCalendar.template -v
*** INITIAL OPTIONS:
    username: superman
    password: Kryptonite
    daysahead: 7
    startdate: None
    enddate: None
    allevents: True
    wordsearch: None
    limit: 0
    template: /usr/share/conkygooglecalendar/conkyGoogleCalendar.template
    dateformat: None
    indent: 0
    nowho: False
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching all event data...
INFO: Processing output...
Title: Spring Quarter Ends
Start Time: Sat 06/13/2009

Title: Summer Quarter Starts
Start Time: Mon 06/22/2009

```
For some reason it's giving me events from two months in the future.  Any guess as to why?

---

### Post by kaivalagi on 2009-04-13
> **mockdeep said:**
> I'm having a problem getting it to use the proper date:

```
$conkyGoogleCalendar -u superman -p Kryptonite [COLOR="Red"]**-a**[/COLOR] -r "Super Man" --template=/usr/share/conkygooglecalendar/conkyGoogleCalendar.template -v
*** INITIAL OPTIONS:
    username: superman
    password: Kryptonite
    daysahead: 7
    startdate: None
    enddate: None
    [COLOR="Red"]**allevents: True**[/COLOR]
    wordsearch: None
    limit: 0
    template: /usr/share/conkygooglecalendar/conkyGoogleCalendar.template
    dateformat: None
    indent: 0
    nowho: False
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching all event data...
INFO: Processing output...
Title: Spring Quarter Ends
Start Time: Sat 06/13/2009

Title: Summer Quarter Starts
Start Time: Mon 06/22/2009

```
For some reason it's giving me events from two months in the future.  Any guess as to why?

I think the allevents option (-a) you have is the cause...this overrides the default 7 days ahead one...you need to explicitly define ONE of the options. Lose the "-a" and add "-d 14" to your command line instead to get the next 14 days for example

Hope that helps

---

### Post by mockdeep on 2009-04-13
> **kaivalagi said:**
> I think the allevents option (-a) you have is the cause...this overrides the default 7 days ahead one...you need to explicitly define ONE of the options. Lose the "-a" and add "-d 14" to your command line instead to get the next 14 days for example

Hope that helps

That fixed it.  Thanks!  Great script.

---

### Post by nauska on 2009-04-15
First, thank you for your script!

Second, unfortantly I have a problem with getting all of my calendar events. I have imported a calendar from my school in iCal format using the "Add by URL" option in Google Calendar. These events won't show up in conky. Is there any way to get these events to show up? I can give you the URL to the calender if it helps.

All other calendars seems to work fine.

Thank you for your help!

---

### Post by kaivalagi on 2009-04-15
> **nauska said:**
> First, thank you for your script!

Second, unfortantly I have a problem with getting all of my calendar events. I have imported a calendar from my school in iCal format using the "Add by URL" option in Google Calendar. These events won't show up in conky. Is there any way to get these events to show up? I can give you the URL to the calender if it helps.

All other calendars seems to work fine.

Thank you for your help!

Yep, give me the url for the ical based calendar and I'll add it to a test calendar and see what happens...

It may be a limitation with the gdata api??? let's hope not...otherwise there is nothing I can do about it

---

### Post by nauska on 2009-04-15
Thanks!

The calendar (my school schedule :) ) can be found at:

[http://timeedit.ita.chalmers.se/4DACTION/iCal_downloadReservations/timeedit.ics?from=902&to=924&id1=11466000&id2=370000&id3=13109000&id4=11180000&branch=1&lang=2]("http://timeedit.ita.chalmers.se/4DACTION/iCal_downloadReservations/timeedit.ics?from=902&to=924&id1=11466000&id2=370000&id3=13109000&id4=11180000&branch=1&lang=2")

Just add the URL in Google Calendar.

---

### Post by kaivalagi on 2009-04-15
> **nauska said:**
> Thanks!

The calendar (my school schedule :) ) can be found at:

[http://timeedit.ita.chalmers.se/4DACTION/iCal_downloadReservations/timeedit.ics?from=902&to=924&id1=11466000&id2=370000&id3=13109000&id4=11180000&branch=1&lang=2]("http://timeedit.ita.chalmers.se/4DACTION/iCal_downloadReservations/timeedit.ics?from=902&to=924&id1=11466000&id2=370000&id3=13109000&id4=11180000&branch=1&lang=2")

Just add the URL in Google Calendar.

I can confirm that once added the calendar **_does_** show when the script is run...I didn't change any default settings, i.e. the calendar is not made public...

I ran the script with specific start and end dates to ensure I would see something appropriate.

So once the iCal calendar is added try running the below and see whether you get your AI Supervision appointment :)

```
conkyGoogleCalendar --username=USERNAME --password=PASSWORD -s 2009-04-20 -e 2009-04-22
```

If that works then you know there are some argument tweaks necessary...things that may trip you up are:

[LIST]
[*]--limit stopping later appointments from showing up
[*]--daysahead option used isn't far enough ahead
[*]--requestCalendarNames option used without the necessary addition for the new calendar you just added
[/LIST]

Hope that helps...

---

### Post by nauska on 2009-04-15
When running that, I get the following error
```
ERROR: getDateRangedEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}
No Events...

```

To get my other calendars I use (in .conkyrc)
```
${execpi 1800 conkyGoogleCalendar -u user -p password -r "Blandat;Gym;Skola;Swedish Holidays" --template=/home/nauska/conkyGoogleCalendar.template -n -d 28}
```

All of them show up except "Skola" which is the calender above.

---

### Post by kaivalagi on 2009-04-15
> **nauska said:**
> When running that, I get the following error
```
ERROR: getDateRangedEvents:Unexpected error:{'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}
No Events...

```

I debugged what's going on...and even though you changed the name of the calendar from "TimeEdit" to "Skola" the feed data which is retrieved has the calendar still named as "TimeEdit". As the script is using looking for a match on the calendar names in the feed it can't find "Skola" and so the required calendar isn't displayed.

For now used the name "TimeEdit" in your script settings and it should work.

When I get time I'll look into interrogating the feed data in more detail, it looks like when a calendar is renamed the main name stays and an addition xml tag is added to the feed data...e.g.

```
<ns1:overridename value="**Skola**" xmlns:ns1="http://schemas.google.com/gCal/2005" />
```

I need to extract this name as well as the original and search for either when the -r option is used.

Hope that helps

P.S. Can you determine which calendar is causing the nasty error when you don't use the -r option? If it is a public one I can add I wouldn't mind trying to figure out that issue too.........

---

### Post by nauska on 2009-04-15
That solved my problem! Thank you again!

If I import several calendars from TimeEdit, do you think all of them will have the same main name? How can I see the main name of a calendar once I have renamed it? I have some calendars that I have been invited to see by others. Is it possible to add these calendars as well?

For the error message, I think it might be caused by the Weather calendar. I get the same error message when I run
```
conkyGoogleCalendar --username=user --password=pass -r "Weather"
```

---

### Post by kaivalagi on 2009-04-15
> **nauska said:**
> That solved my problem! Thank you again!

If I import several calendars from TimeEdit, do you think all of them will have the same main name? How can I see the main name of a calendar once I have renamed it? I have some calendars that I have been invited to see by others. Is it possible to add these calendars as well?

For the error message, I think it might be caused by the Weather calendar. I get the same error message when I run
```
conkyGoogleCalendar --username=user --password=pass -r "Weather"
```

Can you provide a link to the weather calendar so I can add the exact same one?

The original name is always shown in the settings page of the calendar in question.

I have updated the script to handle overridden names when they are set. If a name is overridden this is used to match against instead of the default name...

Give the attached a go by using your named calendar "Skola" and let me know how you get on :) I had to get busy with the xml dom...bloody xml namespaces!

If all works out I'll release an update in the next day or so...

---

### Post by nauska on 2009-04-15
> Can you provide a link to the weather calendar so I can add the exact same one?

The weather calendar is added through the settings in google calendar. Click on the settings link in the top right corner and look for "Show weather based on my location".

> The original name is always shown in the settings page of the calendar in question.

I can't seem to find it in the settings for that calendar. The only thing regarding the name is the "Calendar Name" field, which shows my name for it (Skola and not TimeEdit). Can you point me in the right direction?

> I have updated the script to handle overridden names when they are set. If a name is overridden this is used to match against instead of the default name...

Give the attached a go by using your named calendar "Skola" and let me know how you get on :) I had to get busy with the xml dom...bloody xml namespaces!

If all works out I'll release an update in the next day or so...

I get the two entries (from 2004-04-21 as expected), as well as a lot of xml-code before the two entries. So it kind of works, but not 100% :)

---

### Post by kaivalagi on 2009-04-15
> **nauska said:**
> The weather calendar is added through the settings in google calendar. Click on the settings link in the top right corner and look for "Show weather based on my location".

I'll take a look, thanks

> **nauska said:**
> I can't seem to find it in the settings for that calendar. The only thing regarding the name is the "Calendar Name" field, which shows my name for it (Skola and not TimeEdit). Can you point me in the right direction?

It was shown when I first edited the name, but now it is not shown. SO much for that....as long as you use the current name it should work fine ;)

> **nauska said:**
> I get the two entries (from 2004-04-21 as expected), as well as a lot of xml-code before the two entries. So it kind of works, but not 100% :)

My bad :) I left a print statement in when I was looking at the xml content...I'll get the package sorted any moment and you should then be able to receive an update through apt instead...I'll post again when it's there

---

### Post by kaivalagi on 2009-04-15
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]--maxwidth will set maximum lengths for output lines (default 40 as before)
[*]Updated to handle overridden calendar names when using the --requestCalendarNames option to limit output
[/LIST]

Changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.04_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.04_source.changes)

The first post has been updated and the apt package should be available soon

Cheers

---

### Post by nauska on 2009-04-16
Great, thank you very much! :)

Just one issue at the moment. One of my calendars is called "Blandat" and one of the shared calendars is called "Malin - Blandat" (my own name for that calendar). When I request "Blandat" I get both of them. When I request "Malin - Blandat" I only get that one.

Hmm... I see now that if I request "B" I get all of my calendars that contains the letter B (not case sensitive). I suppose the script does not match the entire string?

---

### Post by kaivalagi on 2009-04-16
> **nauska said:**
> Great, thank you very much! :)

Just one issue at the moment. One of my calendars is called "Blandat" and one of the shared calendars is called "Malin - Blandat" (my own name for that calendar). When I request "Blandat" I get both of them. When I request "Malin - Blandat" I only get that one.

Hmm... I see now that if I request "B" I get all of my calendars that contains the letter B (not case sensitive). I suppose the script does not match the entire string?

No, the script searches for the text in the names. It means that you can name your calendars and retrieve all you want with one name...

Is it a big problem?

---

### Post by nauska on 2009-04-16
> **kaivalagi said:**
> No, the script searches for the text in the names. It means that you can name your calendars and retrieve all you want with one name...

Is it a big problem?

It's not a big problem, but if I only want to show entries from "Blandat", I have to rename "Malin - Blandat" (or "Blandat") to something else.

---

### Post by kaivalagi on 2009-04-16
**[COLOR="Purple"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Changed the default connection timeout from 10 to 30 seconds
[*]Calendars detailed in the --requestCalendarNames option now HAVE to match the exact name (not case sensitive though) e.g. -r "Diary" will no longer mean a calendar called "SchoolDiary" is output, to output it -r "SchoolDiary" is necessary.
[/LIST]

Changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.05_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkygooglecalendar_2.05_source.changes)

The first post has been updated and the apt package should be available soon

Cheers

---

### Post by nauska on 2009-04-16
Thank you, once again! This script is really nice, and I can't stop configuring it in different ways to suit my needs :)

Keep up the good work, and take some time off this weekend ;)

---

### Post by kaivalagi on 2009-04-16
> **nauska said:**
> Thank you, once again! This script is really nice, and I can't stop configuring it in different ways to suit my needs :)

Keep up the good work, and take some time off this weekend ;)

I just had too many outstanding things to get checked in and published...not many loose ends left now, my gtk app just got a major update too...you might want to check it out...see my sig

Oh yes, I will take some time out now the weather is getting better..I'll be doing geeky photography and nitro car bashing with my son instead :)

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps for conky scripts have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by nauska on 2009-04-22
It's me again ;)

I have an event that goes for the whole day (in the top of Google Calendar). When I call your script with
```
conkyGoogleCalendar -u user -p pass -r "Calendar1" --dateformat="" --timeformat="%H:%M" -n -d 1
```
I still get the date for that event. The output is
```
My Event
22/04/09 - 23/04/09
```
with todays date and tomorrows date, even though I have added --dateformat="". All other events (with a start time and an end time) work as expected.

---

### Post by kaivalagi on 2009-04-22
> **nauska said:**
> It's me again ;)

I have an event that goes for the whole day (in the top of Google Calendar). When I call your script with
```
conkyGoogleCalendar -u user -p pass -r "Calendar1" --dateformat="" --timeformat="%H:%M" -n -d 1
```
I still get the date for that event. The output is
```
My Event
22/04/09 - 23/04/09
```
with todays date and tomorrows date, even though I have added --dateformat="". All other events (with a start time and an end time) work as expected.

If an event has both a date and time part to it, setting the dateformat to "" means only the time comes through. However if there is no time part the dateformat = "" does nothing otherwise there is nothing to output at all.

Here's the code for the formatting of datetime, the green is the code kicking in for the event you have posted:

```
                [COLOR="Green"]if dateandtime == True:[/COLOR]
                    if self.dateformat == "":
                        whendatetime = whendatetime.strftime(self.timeformat)
                    else:
                        whendatetime = whendatetime.strftime(self.dateformat + " " + self.timeformat)
                [COLOR="Green"]else:
                    if self.dateformat == "": # if no formating but only required to show date we need then revert to default!
                        whendatetime = whendatetime.strftime(locale.nl_langinfo(locale.D_FMT))[/COLOR]
                    else:
                        whendatetime = whendatetime.strftime(self.dateformat)
```

---

### Post by nauska on 2009-04-22
Thank you! Changed it so it will suit my needs :)

Keep up the good work!

---

### Post by rayok on 2009-04-25
Hello! Thanks for conkyGoogleCalendar script but I get the following error(s) when running through conky or just plain command line. I already have override_utf8_locale yes in my .conkyrc. Also, I installed using the .deb and running a near-vanilla Jaunty install.. Hmm..

```

$ conkyGoogleCalendar --username=username@gmail.com --password=password

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc2 in position 29: ordinal not in range(128)

```

---

### Post by kaivalagi on 2009-04-26
> **rayok said:**
> Hello! Thanks for conkyGoogleCalendar script but I get the following error(s) when running through conky or just plain command line. I already have override_utf8_locale yes in my .conkyrc. Also, I installed using the .deb and running a near-vanilla Jaunty install.. Hmm..

```

$ conkyGoogleCalendar --username=username@gmail.com --password=password

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
ERROR: writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc2 in position 29: ordinal not in range(128)

```

I thought this issue was resolved already...

A particular character in your calendar is a non-standard one and is causing the script to get confused. Any chance of narrowing down the offending event data using --startdate and --enddate options to limit the output, and then pass on the snippet of text which is non-standard?

---

### Post by rayok on 2009-04-26
> **kaivalagi said:**
> I thought this issue was resolved already...

A particular character in your calendar is a non-standard one and is causing the script to get confused. Any chance of narrowing down the offending event data using --startdate and --enddate options to limit the output, and then pass on the snippet of text which is non-standard?

Ahh so it was something in "my" calendar. After knowing that I poked around with my calendar settings and since I don't have any events for the next 7+ days it had to be something else. It's the public weather calendar! And just unchecking the 'show in list' option doesn't do it. I had to unsubscribe. Interesting.. Thanks for your help kaivalagi! :)

---

### Post by kaivalagi on 2009-04-27
> **rayok said:**
> Ahh so it was something in "my" calendar. After knowing that I poked around with my calendar settings and since I don't have any events for the next 7+ days it had to be something else. It's the public weather calendar! And just unchecking the 'show in list' option doesn't do it. I had to unsubscribe. Interesting.. Thanks for your help kaivalagi! :)

You can keep subscribed to the weather calendar, and use the -r option for the script, telling it which calendars you want it to display for.

---

### Post by kenji_ogami on 2009-05-01
Thank you kaivalagi, very nice script.
Unfortunately I get this error: "writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 57: ordinal not in range 128. Override_utf8_locale is set to yes, I didn't add any public calendar. My OS is Debian Lenny, i think the problem started since I upgraded the script but I'm not sure :(

---

### Post by kaivalagi on 2009-05-02
> **kenji_ogami said:**
> Thank you kaivalagi, very nice script.
Unfortunately I get this error: "writeOutput:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 57: ordinal not in range 128. Override_utf8_locale is set to yes, I didn't add any public calendar. My OS is Debian Lenny, i think the problem started since I upgraded the script but I'm not sure :(

This is the biggest problem I have with python, string and unicode type conversion...when I get a spear couple of days I'll need to go through the code line by line to understand where things might be going wrong. This might be some time off yet...

Can I suggest you try to isolate the troublesome calendar entries for now and try and work around it...it will be because a non ascii character is in the calendar entry content

---

### Post by DouglasCaixeta on 2009-05-12
Hi,

Is there an easy way to change the script, and retrieve only the Title of the event, instead all the times and everything?

---

### Post by kaivalagi on 2009-05-13
> **DouglasCaixeta said:**
> Hi,

Is there an easy way to change the script, and retrieve only the Title of the event, instead all the times and everything?

Yep, first of all take a copy of the example template and conkyrc here: /usr/share/conkygooglecalendar/example . Get that working for you, then remove all the markers from the template you don't want (key words in square brackets)

The default template looks similar to the example, i.e. it has all the bits of info in it like below:

```
${color3}Title: ${color1}[title]
${color3}Start Time: ${color1}[starttime]
${color3}End Time: ${color1}[endtime]
${color3}Location: ${color1}[location]
${color3}Description: ${color1}[description]
${color3}Who: ${color1}[who]

```

If you define a new template and use it through the --template option, you could have it simply like this:

```
[title]

```

From the command line help, the --template or -t option:

```
  -t FILE, --template=FILE
                        Template file determining the format for each event.
                        Use the following placeholders: [title], [starttime],
                        [endtime], [location], [description], [who]. Ensure
                        only one placeholder per line, as the whole line is
                        removed if no data for that placeholder exists.
```

Hope that helps

---

### Post by DouglasCaixeta on 2009-05-13
Thank you!

---

### Post by bearman on 2009-05-23
Great script I have been using it for a while now. I am having one problem though. I have it set up to retrieve events for a certain day, like tomorrow, 2 days from now, 3, etc. If an event is late enough in the day it shows up on multiple days. It seems to me like a timezone issue but I can figure out how to correct it. 

Thanks for the help, and the great scripts.

BEARMAN

---

### Post by mbottrell on 2009-06-02
Firstly, a big thank you to [kaivalagi](http://ubuntuforums.org/member.php?u=494551) and the awesome conky scripts you have put in place.  

I'm using a number of them,  namely:
[LIST]
[*]conkyemail
[*]conkyforecast
[/LIST]

I am attempting to get conkygooglecalendar working but alas, without much luck.  

I'm wondering if anyone else has had this error?   
**ERROR: GoogleCalendarEngine Initialisation:Unexpected error:sendall**

(I've searched the forums but can't find any reference to it).  :(

```
$ conkyGoogleCalendar -u username@gmail.com -p mypass -r "Calendar1" --dateformat="%a %d/%m/%y" --timeformat="%H:%M" -n -d 3
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/var/lib/python-support/python2.6/atom/http.py:225: DeprecationWarning: socket.ssl() is deprecated.  Use ssl.wrap_socket() instead.
  ssl = socket.ssl(p_sock, None, None)
/var/lib/python-support/python2.6/atom/http.py:226: DeprecationWarning: FakeSocket is deprecated, and won't be in 3.x.  Use the result of ssl.wrap_socket() directly instead.
  fake_sock = httplib.FakeSocket(p_sock, ssl)
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:sendall
No Events...

```

Any ideas people?

For the record this is Jaunty x86_64.

---

### Post by GonZo on 2009-06-03
I get a similar error to WriteOutput error but is something related to templates

```
$ conkyGoogleCalendar -an -u ******** -p ******** -l 7 -r "Cumpleaños y aniversarios" -F "%H:%m" -t /home/gonzalo/.conkyscripts/conkyGoogleCalendar.config
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)

ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)

ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 6: ordinal not in range(128)
```

I've tried to add "override_utf8_locale yes" to my conkyrc file with no luck.

This is my locale
```
$ locale
LANG=es_ES.UTF-8
LC_CTYPE="es_ES.UTF-8"
LC_NUMERIC="es_ES.UTF-8"
LC_TIME="es_ES.UTF-8"
LC_COLLATE="es_ES.UTF-8"
LC_MONETARY="es_ES.UTF-8"
LC_MESSAGES="es_ES.UTF-8"
LC_PAPER="es_ES.UTF-8"
LC_NAME="es_ES.UTF-8"
LC_ADDRESS="es_ES.UTF-8"
LC_TELEPHONE="es_ES.UTF-8"
LC_MEASUREMENT="es_ES.UTF-8"
LC_IDENTIFICATION="es_ES.UTF-8"
LC_ALL=

```

It seems it's something related to getOutputFromTemplate function. I've tried to encode to utf8 returned value but with no luck.

Any ideas?

---

### Post by kaivalagi on 2009-06-03
> **mbottrell said:**
> 

Any ideas people?

For the record this is Jaunty x86_64.

None sorry, never seen that issue before

---

### Post by kaivalagi on 2009-06-03
> **GonZo said:**
> 
It seems it's something related to getOutputFromTemplate function. I've tried to encode to utf8 returned value but with no luck.

Any ideas?

Can you post the template so I can attempt to reproduce the problem and debug the code?

---

### Post by Bruce M. on 2009-06-03
EDIT: Oops! I see your on it K.

So sorry!
Bruce

---

### Post by kaivalagi on 2009-06-03
> **Bruce M. said:**
> EDIT: Oops! I see your on it K.

So sorry!
Bruce

Be my guest, I can only spend a little time right now, I am at work....:o

---

### Post by mbottrell on 2009-06-03
> **mbottrell said:**
> I'm wondering if anyone else has had this error?   
**ERROR: GoogleCalendarEngine Initialisation:Unexpected error:sendall**

(I've searched the forums but can't find any reference to it).  :(


Well some playing around, and I found the culprit.  It seems the **http_proxy** environment variable was set... and it wasn't liked.  :(

Unsetting the proxy setting, and all was happy.  ;)

Hopefully in the future it supports http_proxy and https_proxy configurations.

---

### Post by kaivalagi on 2009-06-03
> **mbottrell said:**
> Unsetting the proxy setting, and all was happy.  ;)


Well found!

---

### Post by mbottrell on 2009-06-03
> **kaivalagi said:**
> Well found!
hehehe... thanks.  :)

Strangely enough both the Email and GoogleCalendar scripts  both seem to support http/https -- yet it's only the Calendar one that borks (with a proxy environment variable set).

Any idea kaivalagi?

---

### Post by kaivalagi on 2009-06-04
> **mbottrell said:**
> hehehe... thanks.  :)

Strangely enough both the Email and GoogleCalendar scripts  both seem to support http/https -- yet it's only the Calendar one that borks (with a proxy environment variable set).

Any idea kaivalagi?

The email script uses standard libraries to handle email protocols and so supports all the standard proxy stuff too...

The google calendar script uses the gdata api supplied by google, this is more custom and so I guess has trouble with proxies...?

Really, the questions you are asking need to be directed at google, I am just using their api...

---

### Post by GonZo on 2009-06-04
> **kaivalagi said:**
> Can you post the template so I can attempt to reproduce the problem and debug the code?

Hello kaivalagi,

   here you have the template. As you can see it's very simple.

```

Title: [title]
Location: [location]
Starting: [starttime]
Ending: [endtime]
Description: [description]
```

Here you have too the complete conkyrc file, I'm sure most of staff has no importance but I want to provide you as much information as you need:

```
# Events List

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont unDotum:size=10
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 10
 
# Minimum size of text area
minimum_size 354 5
maximum_width 258

# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors 
default_color 626262

# Text alignment, other possible values are commented
alignment top_left

# Gap between borders of screen
gap_x 1290
gap_y 554
 
# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
 
TEXT

${color e0c969}${hr 2,400}
${voffset -43}$color${font A bite:size=24}EVENTS$font
${execpi 1800 conkyGoogleCalendar -an -u ***** -p ******** -r "Cumpleaños y aniversarios;Go*****ao;VEU" -F "%H:%m" -t /home/*****/.conkyscripts/conkyGoogleCalendar.config} 
```


I called this with the next command

```
$conky -d -c /home/*****/.conkyscripts/conkyrc3 &
```

Inside conky or through console I get the same error:
```

conky -d -c /home/*****/.conkyscripts/conkyrc3 &
[1] 17405
******@richard:~$ Conky: forked to background, pid is 17406

Conky: desktop window (14000ac) is subwindow of root window (97)
Conky: window type - override
Conky: drawing to created window (0x5600001)
Conky: drawing to double buffer
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)
ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 21: ordinal not in range(128)
ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)
ERROR: getOutputFromTemplate:Unexpected error:'ascii' codec can't decode byte 0xc3 in position 6: ordinal not in range(128)
```

And I get no information (empty exit) in conky window, when I should see something like...
```

Title: Fefeto
Starting: 5/6/2009 10:00am
Ending: 5/6/2009 11:00am
```

...which is a weekly meeting. Few days ago the script showed at least the first meeting as follows...

```
Title: Misa Yayo
Starting: 5/6/2009 10:00am
Ending: 5/6/2009 11:00am

```
...which is a standard meeting.

I've tried to move the standard meeting to tomorow and it shows that first meeting again but next meetings (standard or repetitive) doesn't appear.

Sorry if my english isn't very correct and thanks for your help. 

See you...

---

### Post by kaivalagi on 2009-06-04
> **GonZo said:**
> 
And I get no information (empty exit) in conky window, when I should see something like...
```

Title: Fefeto
Starting: 5/6/2009 10:00am
Ending: 5/6/2009 11:00am
```

...which is a weekly meeting. Few days ago the script showed at least the first meeting as follows...

```
Title: Misa Yayo
Starting: 5/6/2009 10:00am
Ending: 5/6/2009 11:00am

```
...which is a standard meeting.

I've tried to move the standard meeting to tomorow and it shows that first meeting again but next meetings (standard or repetitive) doesn't appear.

Sorry if my english isn't very correct and thanks for your help. 

See you...

Don't worry, you're making more sense than some of my work colleagues :)

Does the meeting that causes the problem have any extended characters in the text, that are not part of the standard ascii set? It might be this that is causing the issues...just good to know so I can fully reproduce the issue.

[COLOR="Navy"]Edit: Nevermind, all was fine until I created a meeting with accented characters in the name...bloody unicode again...

I think I have it working now but can't be sure I haven't broken other text support in the process, it should be okay but...I've attached a deb file you can install with. Can you install it and let me know if all is good afterwards...I'll then publish the new version[/COLOR]

---

### Post by mbottrell on 2009-06-04
> **kaivalagi said:**
> Really, the questions you are asking need to be directed at google, I am just using their api...

No probs.  It wasn't a complaint just clarification of point.  ;)

---

### Post by kaivalagi on 2009-06-05
> **mbottrell said:**
> No probs.  It wasn't a complaint just clarification of point.  ;)

Didn't take it any other way :)

---

### Post by GonZo on 2009-06-05
> **kaivalagi said:**
> 
[COLOR="Navy"]Edit: Nevermind, all was fine until I created a meeting with accented characters in the name...bloody unicode again...

I think I have it working now but can't be sure I haven't broken other text support in the process, it should be okay but...I've attached a deb file you can install with. Can you install it and let me know if all is good afterwards...I'll then publish the new version[/COLOR]

Hi kaivalagi,

    we almost have it solved!. I've instaled your patch and executing the command I get an error.

```
ERROR: Template file no found!
```

I've tested (with cat) that path to the template file is correct and accesible. Looking inside conkyGoogleCalendar.py it seems the error is launched from this code:

```
                # load the template file contents
                try:
                    fileinput = codecs.open(os.path.expanduser(self.options.template), encoding='utf-8')
                    template = fileinput.read()
                    fileinput.close()
                    # lose the final "\n" which should always be there...
                    template = template[0:len(template)-1]
                except:
                    self.logError("Template file no found!")
                    sys.exit(2)

```

...which seems correct . Well, I recognize that I'm not an python autority :D. (something different to previous code?)

Then I've tried to drop out my own template and use the default and... **BANG, it works!!**

```
$conkyGoogleCalendar -an -u ***** -p ******** -r "Cumpleaños y aniversarios;G******o;VEU" -F "%H:%m" 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Title: D****
Start Time: mié 10/06/09 19:06
End Time: mié 10/06/09 20:06

Title: 1****************************** I
Start Time: vie 12/06/09 12:06
End Time: vie 12/06/09 13:06

Title: Día en *****************yte
Start Time: sáb 27/06/09
End Time: dom 28/06/09

Title: Revisión*********A
Start Time: jue 26/11/09 10:11
End Time: jue 26/11/09 10:11
Description: Le recordamos que su cita para la revisi...

```

So, apart from the template file error (which I supose is a mess), it works like a charm for "standard" events. Thanks! I'll be pleased to test additional patches if you want.

The only thing I missed are periodical events, for example aniversaries. Are you planning to support this kind of events?

PD: I've detected an ¿error?: using -d parameter doesn't work. Always retrieves all events.

Thanks for your patient and I encourage you to continue developing this soft.

---

### Post by mbottrell on 2009-06-05
> **kaivalagi said:**
> Didn't take it any other way :)

Ahh good...   :) 
Lack of tone is always a concern on forums/SMS/Email. 

Once again, a big thanks for your great work on the scripts, and the followup work on support you've provided.  :KS

---

### Post by kaivalagi on 2009-06-05
> **GonZo said:**
> Hi kaivalagi,

    we almost have it solved!. I've instaled your patch and executing the command I get an error.

```
ERROR: Template file no found!
```


I've attached a new package, this should sort out the template file loading issue

> **GonZo said:**
> 
The only thing I missed are periodical events, for example aniversaries. Are you planning to support this kind of events?

Should be supported...repeating events should show :confused:
I'll have a play over the next few days

> **GonZo said:**
> 
PD: I've detected an ¿error?: using -d parameter doesn't work. Always retrieves all events.

-d option working for me, set it to 4 and I only see the next 4 days of events (including today)

> **GonZo said:**
> 
Thanks for your patient and I encourage you to continue developing this soft.

No problem, keep the issues coming, this is the best testing the script has had since it was first created

---

### Post by GonZo on 2009-06-05
> **kaivalagi said:**
> Should be supported...repeating events should show :confused:
I'll have a play over the next few days

-d option working for me, set it to 4 and I only see the next 4 days of events (including today)


Don't worry about this. It was my problem.

I've founded the reason for both problems, using -d parameter and getting periodical events. Pay atention to the command I've been using.

```

$conkyGoogleCalendar **-an** -u ******* -p ******** -r "Cumpleaños y aniversarios;G********o;VEU" -F "%H:%m"
```

The key is the use of -a parameter. I've realized that -a parameter is opposed to -d. Surprisely when I've changed it to "-d 15" I've got all the periodical events!!! So it works! It works!

```
$ conkyGoogleCalendar **-n -d 15** -u ******* -p ********* -r "Cumpleaños y aniversarios;G*****o;VEU" -F "%H:%m" 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Title: Cumpleaños Y***
Start Time: lun 08/06/09
End Time: mar 09/06/09

Title: Aniversario Jo** y P***
Start Time: mié 10/06/09
End Time: jue 11/06/09

Title: Dieta
Start Time: mié 10/06/09 19:06
End Time: mié 10/06/09 20:06

Title: 1er ejercicio ***** en el *****o I
Start Time: vie 12/06/09 12:06
End Time: vie 12/06/09 13:06

Title: Revisar nivel de agua del coche
Start Time: lun 15/06/09 20:06
End Time: lun 15/06/09 21:06

Title: Cumpleaños M**********
Start Time: jue 18/06/09
End Time: vie 19/06/09

```

> I've attached a new package, this should sort out the template file loading issue

It seems that python doesn't like my templates :( . After solving previous errors I've tried to link my template getting next error:


```
~$ conkyGoogleCalendar -d 7 -u [...] -t /home/*****/.conkyscripts/conkyGoogleCalendar.config

[...Boring stuff: Deprecating Warning...]

ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 372, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 7: ordinal not in range(128)


ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 390, in getOutputFromTemplate
    output = output.replace("[starttime]",starttime)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)


ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 390, in getOutputFromTemplate
    output = output.replace("[starttime]",starttime)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)
```

Then I thought maybe it was the typical problem:"it's not you it's me", and tried to used the example template stored in /usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template as follows: 

```
$ conkyGoogleCalendar -d 7 [...] -t /usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template 

[...boring stuff...]

ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 372, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 7: ordinal not in range(128)


ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 390, in getOutputFromTemplate
    output = output.replace("[starttime]",starttime)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)


ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 390, in getOutputFromTemplate
    output = output.replace("[starttime]",starttime)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 2: ordinal not in range(128)

```

It seems UTF-8 issues are comming back again!! I've tried to copy this template file to a user folder, been sure that the codification is UTF-8, but I've got the same result.

> No problem, keep the issues coming, this is the best testing the script has had since it was first created

Thanks a lot! Now I feel very motivated!

I've attached an image of my desktop were you can see the result using your last deb without any template file. I thinks it's amazing!

---

### Post by kaivalagi on 2009-06-05
> **GonZo said:**
> It seems UTF-8 issues are comming back again!! I've tried to copy this template file to a user folder, been sure that the codification is UTF-8, but I've got the same result.

I'll see what I can figure out over the next couple of days, I get the feeling it is not the template itself but the replacement of [...] with unicode text

> **GonZo said:**
> I've attached an image of my desktop were you can see the result using your last deb without any template file. I thinks it's amazing!

Nice desktop, very artistic!

---

### Post by adelodder on 2009-06-16
I have been succesfully using conkyGoogleCalendar on Debian Lenny for a while by adding 
```
deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main
```
to my /etc/apt/sources.list and installing it from there.

These days though, when I run this command:
```
conkyGoogleCalendar -u xxxxxxxx@gmail.com -p xxxxXXxxxX  -d 30 -l 10 -f "%a %d/%m/%y" -F "%H:%M" -t ~/.config/conky/conkyGoogleCalendar
```

I get the following error message:
```
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:{'status': 400, 'body': 'Invalid value for Cache-Control option 'max-stale'', 'reason': 'Bad Request'}
No Events...
```

The only reference I could find to this error was from here:
[http://code.google.com/p/google-shared-contacts-client/updates/list#]("http://code.google.com/p/google-shared-contacts-client/updates/list#")

Any idea what that might mean.  I very much liked using conkyGoogleCalendar.  Hopefully it was not the last time it worked on Debian Lenny.

Many thanks anyway

---

### Post by Crashmaxx on 2009-06-19
Been using this great little program for a while now. But I finally upgraded to Jaunty and now I get this error when I start conky:
```

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

```
Any ideas?

---

### Post by kaivalagi on 2009-06-20
> **Crashmaxx said:**
> Been using this great little program for a while now. But I finally upgraded to Jaunty and now I get this error when I start conky:
```

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

```
Any ideas?

It's not an error, it's a warning. I get it too...

I think it is probably something to do with the python-gdata package used to talk to the google calendar api. It will be using the sha module rather than the hashlib one...something probably got changed in the python 2.6 libraries - hence turning up when yu upgraded to Jaunty.

Don't worry about it........

---

### Post by Crashmaxx on 2009-06-20
> **kaivalagi said:**
> It's not an error, it's a warning. I get it too...

I think it is probably something to do with the python-gdata package used to talk to the google calendar api. It will be using the sha module rather than the hashlib one...something probably got changed in the python 2.6 libraries - hence turning up when yu upgraded to Jaunty.

Don't worry about it........

OK, then why does it only display this now:
```

<start time>
<title>
<start time>
<title>
<start time>
<title>

```
Thanks.

---

### Post by kaivalagi on 2009-06-20
> **Crashmaxx said:**
> OK, then why does it only display this now:
```

<start time>
<title>
<start time>
<title>
<start time>
<title>

```
Thanks.

I have no idea, but it is unrelated

For example when I run:

```
conkyGoogleCalendar -u ******* -p ******* -d 4 -r Homeserve
```

I get in the terminal (conky output should exclude the warning message):

```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Title: MB Team - Dev Pickup
Start Time: Mon 22/06/09
End Time: Sat 27/06/09
Location: Our Desks
Description: Our teams turn for ME request "dev picku...
Who: robert.farley, michael.neale, james.macl...

Title: Flex Day
Start Time: Mon 22/06/09
End Time: Tue 23/06/09
Who: kaivalagi

Title: Review of the 4.8 release process
Start Time: Tue 23/06/09 09:30:00
End Time: Tue 23/06/09 10:30:00
Location: HGP Meeting Room (1-3) - Elm Hill - Capa...
Description: We need to discuss suggested improvement...
Who: tim.bates, suhel.khan, andrew.viner, dav...

Title: Discuss SQL Server Migration for Mercury
Start Time: Tue 23/06/09 10:30:00
End Time: Tue 23/06/09 11:30:00
Location: HGP Meeting Room (G-2) - Castle - Capaci...
Description: Hi AllI need your combined assistance ...
Who: tim.bates, suhel.khan, andrew.viner, pet...

Title: Daily Review
Start Time: Tue 23/06/09 13:30:00
End Time: Tue 23/06/09 14:00:00
Location: HGP Meeting Room (1-3) - Elm Hill - Capa...
Who: lucy.lawrence, tim.bates, andrew.viner, ...

```

If you're using a template file try pointing to the example one instead to test things out and eliminate issues, to do that use the following option in the call:

```
--template=/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template
```

The warning message is happening for quite a few apps, it relates to python 2.6 in 9.04...do a search on google for the text, you'll see what I mean

Hope that helps

---

### Post by Crashmaxx on 2009-06-20
> **kaivalagi said:**
> I have no idea, but it is unrelated

For example when I run:

```
conkyGoogleCalendar -u ******* -p ******* -d 4 -r Homeserve
```

I get in the terminal (conky output should exclude the warning message):

```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Title: MB Team - Dev Pickup
Start Time: Mon 22/06/09
End Time: Sat 27/06/09
Location: Our Desks
Description: Our teams turn for ME request "dev picku...
Who: robert.farley, michael.neale, james.macl...

Title: Flex Day
Start Time: Mon 22/06/09
End Time: Tue 23/06/09
Who: kaivalagi

Title: Review of the 4.8 release process
Start Time: Tue 23/06/09 09:30:00
End Time: Tue 23/06/09 10:30:00
Location: HGP Meeting Room (1-3) - Elm Hill - Capa...
Description: We need to discuss suggested improvement...
Who: tim.bates, suhel.khan, andrew.viner, dav...

Title: Discuss SQL Server Migration for Mercury
Start Time: Tue 23/06/09 10:30:00
End Time: Tue 23/06/09 11:30:00
Location: HGP Meeting Room (G-2) - Castle - Capaci...
Description: Hi AllI need your combined assistance ...
Who: tim.bates, suhel.khan, andrew.viner, pet...

Title: Daily Review
Start Time: Tue 23/06/09 13:30:00
End Time: Tue 23/06/09 14:00:00
Location: HGP Meeting Room (1-3) - Elm Hill - Capa...
Who: lucy.lawrence, tim.bates, andrew.viner, ...

```

If you're using a template file try pointing to the example one instead to test things out and eliminate issues, to do that use the following option in the call:

```
--template=/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template
```

The warning message is happening for quite a few apps, it relates to python 2.6 in 9.04...do a search on google for the text, you'll see what I mean

Hope that helps
Guess my template's broken. Thanks for pointing me in the right direction.

EDIT: Yeah at some point I guess the template format changed from <> to [] and I was running a really out of date version. All fixed now. Thanks again.

---

### Post by kaivalagi on 2009-06-20
> **Crashmaxx said:**
> Guess my template's broken. Thanks for pointing me in the right direction.

EDIT: Yeah at some point I guess the template format changed from <> to [] and I was running a really out of date version. All fixed now. Thanks again.

No worries, I should have pointed that out, I didn't notice the <> chars...I changed to [] chars when I created my other app which uses the scripts as plugins, so that the <> chars wouldn't interfere with html output - quite some time ago now.

If you check out the example template, you'll be on the right track for sure.

BTW, I know how annoying that warning is, I would love the Ubuntu and/or Google teams to fix things up...python 2.7 maybe...

---

### Post by kaivalagi on 2009-06-27
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Added better stack trace output on error
[*]Fixed (hopefully) unicode support for output
[*]Updated to expand ~ based template paths
[*]Updated to make safe the output to stop unwanted conky execution
[/LIST]

Changes can be found here: [https://launchpad.net/~m-buck/+archive/conky/+files/conkygooglecalendar_2.06_source.changes](https://launchpad.net/~m-buck/+archive/conky/+files/conkygooglecalendar_2.06_source.changes)

The first post is updated and the apt package should be available soon...

---

### Post by Fuut on 2009-07-18
I didn't figure out how the timezones work. Everything that comes back is a hour early. Can someone give me some pointers? I am in Europe/Amsterdam.
Thanks

---

### Post by kaivalagi on 2009-07-18
> **Fuut said:**
> I didn't figure out how the timezones work. Everything that comes back is a hour early. Can someone give me some pointers? I am in Europe/Amsterdam.
Thanks

This is going to be interesting, I am in the GMT+0 timezone which means it is hard for me to test for this problem...

I am assuming you have the correct time zone set in your OS and that other command line functions to give you the time are working properly?
[COLOR="blue"]
**@ALL - Do any users out there living in timezones other than GMT+0 want to help? Any suggestions?**[/COLOR]

---

### Post by Fuut on 2009-07-18
The output of date:
Sat Jul 18 14:00:32 CEST 2009

The output of hwclock --show:
Sat 18 Jul 2009 01:59:56 PM CEST  -0.980892 seconds

And that is the correct time ;)

---

### Post by Bruce M. on 2009-07-19
> **Fuut said:**
> I didn't figure out how the timezones work. Everything that comes back is a hour early. Can someone give me some pointers? I am in Europe/Amsterdam.
Thanks

When you installed Ubuntu did you say "yes" to: "Is your clock set to Universal Time?" (maybe not a direct quote) The answer to select is: Yes that way the clock synchronization service (ntp) will be correct.

Have a nice day.
Bruce

bruloo@bruloo:~$ date
Sun Jul 19 13:14:30 ART 2009
bruloo@bruloo:~$

---

### Post by Fuut on 2009-07-20
I don't know anymore. Is there a way to check that? And is it possible to change if it's wrong?

---

### Post by Jeff Carr on 2009-07-23
For one reason or another, when I alter --timeformat, if my criteria includes either a %M or %m, I recieve the error 
```

sh: Syntax error: Unterminated quoted string

```
and the script exits without a message displayed in conky.  It doesn't seem to matter where in the criteria I put the %M either.  I receive the error when using your example --timeformat="%l:%M %P" as well as any other variant I've tried.

As of right now I'm using python 2.6.2

Any ideas?  This isn't a big problem for me by any means, I just thought I'd let you know.

---

### Post by kaivalagi on 2009-07-24
> **Jeff Carr said:**
> For one reason or another, when I alter --timeformat, if my criteria includes either a %M or %m, I recieve the error 
```

sh: Syntax error: Unterminated quoted string

```and the script exits without a message displayed in conky.  It doesn't seem to matter where in the criteria I put the %M either.  I receive the error when using your example --timeformat="%l:%M %P" as well as any other variant I've tried.

As of right now I'm using python 2.6.2

Any ideas?  This isn't a big problem for me by any means, I just thought I'd let you know.

Can you list your locale, by running "locale" in the terminal

This issue sounds like an issue with that, but to be honest I am not sure how much I can really help...

---

### Post by zeltak on 2009-07-24
Hi

Awesome script

i have a problem that after resuming from sleep (suspend) i get no events even though all the events where there before and it does not refresh...any way to force refresh every xx seconds or force refresh after sleep?

thx alot

Zeltak

---

### Post by Jeff Carr on 2009-07-24
> **kaivalagi said:**
> Can you list your locale, by running "locale" in the terminal

This issue sounds like an issue with that, but to be honest I am not sure how much I can really help...

```
jeffcarr@Battlecat:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

Sure thing, here is my output.... seems consistent at least...  If you have any ideas I'd love to hear them.  I'll do some poking around myself (although python isn't one of the languages I know...).

---

### Post by kaivalagi on 2009-07-24
> **Jeff Carr said:**
> ```
jeffcarr@Battlecat:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```Sure thing, here is my output.... seems consistent at least...  If you have any ideas I'd love to hear them.  I'll do some poking around myself (although python isn't one of the languages I know...).

Nothing obvious, I'm gonna need to play a little.....this may be some time off...

---

### Post by kaivalagi on 2009-07-24
> **zeltak said:**
> Hi

Awesome script

i have a problem that after resuming from sleep (suspend) i get no events even though all the events where there before and it does not refresh...any way to force refresh every xx seconds or force refresh after sleep?

thx alot

Zeltak

Kinda tricky to reproduce, I don't sleep :)

Maybe a general issue with suspending...

---

### Post by k3ttc4r on 2009-07-29
just what i needed to fill the empty space between my weather forecast and the bottom of my screen :D 

anyways, some localization would be great, and i got some trouble with the template file. i get

```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 374, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 13: ordinal not in range(128)

```

---

### Post by Jeff Carr on 2009-07-29
@k3ttc4r If you don't already have it set this way, I'd try putting:
```
override_utf8_locale yes
```
Into your .conkyrc  I think that could potentially solve the problem.

---

### Post by kaivalagi on 2009-07-29
> **k3ttc4r said:**
> just what i needed to fill the empty space between my weather forecast and the bottom of my screen :D 

anyways, some localization would be great, and i got some trouble with the template file. i get

```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 374, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 13: ordinal not in range(128)

```

> **Jeff Carr said:**
> @k3ttc4r If you don't already have it set this way, I'd try putting:
```
override_utf8_locale yes
```Into your .conkyrc  I think that could potentially solve the problem.

Thanks Jeff, just what I would have said...

It could however be the script, I have had serious issues with unicode support in python, it sucks......nothing much I can do about that for now if that is the case....I have way too much on right now.

---

### Post by omnisciencedoggy on 2009-08-13
> **kaivalagi said:**
> I am sure you can still use the start and end date options but construct the dates automatically...

To do this you would want a new script that figures out the dates you need based on todays date, then uses those in calls to the conkyForecast script...

I'll have a look when I get home and onto Linux, I am at work and not infront of a linux PC right now

**===== BEGINNING OF "A" SOLUTION ====================================**

I got a python script which wraps the conkyGoogleCalendar script working. It's not pretty, and you'll need to make a new version of it for each day chunk you want seperately.

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-
from datetime import date, timedelta
import subprocess

STARTDAY = 3 # startday of 0 is today, 1 is tomorrow etc
USERNAME = "???@googlemail.com"
PASSWORD = "???"

startDate = date.today() + timedelta(days=STARTDAY)
endDate = startDate + timedelta(days=1)
subprocess.Popen("conkyGoogleCalendar -u "+USERNAME+" -p "+PASSWORD+" -s "+startDate.strftime("%F")+" -e "+endDate.strftime("%F"),shell=True)[/PHP]

It's fairly self explainatory, you'll need to set values for STARTDAY, USERNAME and PASSWORD. If you want more options added to the calendar script call then the last line needs modifying further...

If you create one script for each day period you want conky output for, you'll get what you need. For an example call I have assumed the script is named getCalStartDay3.py because it gets the events for 3 days ahead, for this you would call it like so:

```
${execi 1800 python /path/to/script/getCalStartDay3.py}
```

I've attached the script too :)

Hope that helps

First off, thank you so much for the wonderful script.  I'm not really a fan of the default and  was hoping what you put in this post would work for me.  For the most part what you describe above works fine, except for when I set the STARTDAY variable to 1 (for showing only the events for tomorrow).  

When I set the STARTDAY variable to 1 I get events from both today and tomorrow.  

It looks to my noobie eyes like the script should be working as intended, but it isn't for some reason.  Any help will be much appreciated.  Thanks in advance!

---

### Post by kaivalagi on 2009-08-14
> **omnisciencedoggy said:**
> First off, thank you so much for the wonderful script.  I'm not really a fan of the default and  was hoping what you put in this post would work for me.  For the most part what you describe above works fine, except for when I set the STARTDAY variable to 1 (for showing only the events for tomorrow).  

When I set the STARTDAY variable to 1 I get events from both today and tomorrow.  

It looks to my noobie eyes like the script should be working as intended, but it isn't for some reason.  Any help will be much appreciated.  Thanks in advance!

Could it be that the today events carry on to tomorrow and that's why they show?

---

### Post by omnisciencedoggy on 2009-08-15
> **kaivalagi said:**
> Could it be that the today events carry on to tomorrow and that's why they show?

I wish it was that simple :(.

I just noticed that it seems to be pushing events after noon (12 pm) on today onto the next day, but not if they are before noon.  

In other words, this morning when I was testing it with events before noon, they would show up as "today" (under --daysahead=1).  Events after noon are showing up as happening tomorrow (--daysahead=2).  

This is happening with the original conkygooglecalendar 2.06 script (I installed it via conkygooglecalendar_2.06_all.deb).

---

### Post by kaivalagi on 2009-08-16
> **omnisciencedoggy said:**
> I wish it was that simple :(.

I just noticed that it seems to be pushing events after noon (12 pm) on today onto the next day, but not if they are before noon.  

In other words, this morning when I was testing it with events before noon, they would show up as "today" (under --daysahead=1).  Events after noon are showing up as happening tomorrow (--daysahead=2).  

This is happening with the original conkygooglecalendar 2.06 script (I installed it via conkygooglecalendar_2.06_all.deb).

Where are you based? I am wondering whether this has anything to do with time zones...???

---

### Post by omnisciencedoggy on 2009-08-16
> **kaivalagi said:**
> Where are you based? I am wondering whether this has anything to do with time zones...???

I'm in Houston, TX - Central United States Time Zone (GMT/UTC - 6h).  It seems like the "day ahead" is just chopping days up at the noon mark instead of midnight mark for me.  

Thank you for all your help!

---

### Post by kaivalagi on 2009-08-16
> **omnisciencedoggy said:**
> I'm in Houston, TX - Central United States Time Zone (GMT/UTC - 6h).  It seems like the "day ahead" is just chopping days up at the noon mark instead of midnight mark for me.  

Thank you for all your help!

This must mean the google calendar api start and stop dates are UTC i.e. expect GMT+0...not sure if I can get a fix out for some time (family hols coming up)

---

### Post by hicke on 2009-08-20
Hi!

I am building a awk/bash/python thing that collects historical events from a special "time reporting calendar" I have created and merges it into a file that gets read by another financial application.

Is there anyway to include historical events in the output? Something like "number of days prior to today".

--daysahead="-10" <<< Note the minus sign...

Even better would be to be able to include a full month:

--monthdata="august" or plain "8" for month number...

Someting like this.

Thanks for a great app!

/Henric

---

### Post by josephellengar on 2009-09-30
Thanks so much to whoever came up with this great script, but I have one question, based on the screenshot I have attached.  Sorry if I'm awakening what is considered a dead thread, but why is my bottom event not showing entirely?  As you can see, the top two events show title, start and end time, and location, but the bottom one only shows title.  Any suggestions?  Thank you!

---

### Post by josephellengar on 2009-09-30
Never mind, I figured it out.  I had to turn off xft.

---

### Post by kaivalagi on 2009-09-30
> **idigchess said:**
> Never mind, I figured it out.  I had to turn off xft.

This thread isn't dead, it's just the script has no real issues :)

Shouldn't be necessary to turn off xft, it may have solved the issue indirectly but not properly.

I think the text_buffer_size needs increasing, look at the Gotchas section in the first post of this thread for more info.

If you have other questions, fire away, I'll be watching :)

---

### Post by josephellengar on 2009-09-30
> **kaivalagi said:**
> This thread isn't dead, it's just the script has no real issues :)

Shouldn't be necessary to turn off xft, it may have solved the issue indirectly but not properly.

I think the text_buffer_size needs increasing, look at the Gotchas section in the first post of this thread for more info.

If you have other questions, fire away, I'll be watching :)

Well whaddaya know!?  It worked!  Thanks man!

---

### Post by Bruce M. on 2009-09-30
> **idigchess said:**
> Well whaddaya know!?  It worked!  Thanks man!

Besides, you'll need that **xtf** for other things.  :)

---

### Post by deh69 on 2009-10-14
Any updates on the UTF-8 error, kaivalagi?

You know,  UnicodeDecodeError cant decode "x" position and such, ordinal not in range (128).

It seems that it screws up the spacing with the entries.

Anyways, just asking. Keep up the good work!

---

### Post by kaivalagi on 2009-10-14
> **deh69 said:**
> Any updates on the UTF-8 error, kaivalagi?

You know,  UnicodeDecodeError cant decode "x" position and such, ordinal not in range (128).

It seems that it screws up the spacing with the entries.

Anyways, just asking. Keep up the good work!

One of these days I'll figure out unicode in python, it seems when I fix it for one thing and alternative problem arises...

I got away from the problem by making a new app which supports html based output instead - but I think most users just want to use conky :)

Work is pretty hectic for the foreseeable and this issue will take quite a bit of investigating, I still have the issue in my todo list though - it's just a time issue right now

Post some example text here which causes you issues when output from your calendar, I'll need it for testing when I get around to taking a proper look again

---

### Post by josephellengar on 2009-10-18
I just changed my google account password and now for some reason, the conky calendar won't update.  I did change the password in the .conkyrc1 file.  My new password is 20 characters, is there a character limit to the password in this script?

---

### Post by kaivalagi on 2009-10-19
> **idigchess said:**
> I just changed my google account password and now for some reason, the conky calendar won't update.  I did change the password in the .conkyrc1 file.  My new password is 20 characters, is there a character limit to the password in this script?

The overall length of the command has limits, try using the short form options i.e. -u instead of --username and -p instead of --password etc.

Run the following to see the equivalent settings:

```
conkyGoogleCalendar -h
```

If that doesn't help then post the command you are using (minus the password)

---

### Post by josephellengar on 2009-10-19
> **kaivalagi said:**
> The overall length of the command has limits, try using the short form options i.e. -u instead of --username and -p instead of --password etc.

Run the following to see the equivalent settings:

```
conkyGoogleCalendar -h
```

If that doesn't help then post the command you are using (minus the password)

I already was using the short equivalent settings.  The TEXT portion of my .conkyrc is:
```

${font Arial:bold:size=10}${color Tan1}SCHEDULE${color DarkSlateGray}${hr 2}${color}${font}
${execi 1000 conkyGoogleCalendar -n -l 10 -d 3 --timeformat="%l:%M %P" -u xxxxxxxxxx -p xxxxxxxxxxxxxxxxxxxx}


```
All I see is the schedule line.
Thanks for your help!

---

### Post by josephellengar on 2009-10-19
When I try to activate or access the script through the command line I get a not found error, but when I try to install it, apt says it is already the newest version.  Strange, no?

---

### Post by kaivalagi on 2009-10-19
> **idigchess said:**
> When I try to activate or access the script through the command line I get a not found error, but when I try to install it, apt says it is already the newest version.  Strange, no?

Running this:
```
ls /usr/bin/conkyGoogleCalendar
```

Should give you this:
```
-rwxr-xr-x 1 root root 133 2008-09-08 23:16 /usr/bin/conkyGoogleCalendar
```

That's the main bin based exec file for kick of things with the python script...

If you look up the conkygooglecalendar in Synaptic and right click and go to the installed files tab, you should see this following listed:

```
/.
/usr
/usr/share
/usr/share/conkygooglecalendar
/usr/share/conkygooglecalendar/example
/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template
/usr/share/conkygooglecalendar/example/conkyrc
/usr/share/conkygooglecalendar/conkyGoogleCalendar.py
/usr/share/pyshared-data
/usr/share/pyshared-data/conkygooglecalendar
/usr/share/doc
/usr/share/doc/conkygooglecalendar
/usr/share/doc/conkygooglecalendar/AUTHORS
/usr/share/doc/conkygooglecalendar/changelog.gz
/usr/share/doc/conkygooglecalendar/README.gz
/usr/share/doc/conkygooglecalendar/copyright
/usr/share/pyshared
/usr/share/pyshared/conkygooglecalendar-2.06.egg-info
/usr/bin
/usr/bin/conkyGoogleCalendar

```

If all of that matches up then I suggest you just run the following (to remove and reinstall it):

```
sudo apt-get remove conkygooglecalendar && sudo apt-get autoclean && sudo apt-get install conkygooglecalendar
```

Hope that helps

---

### Post by josephellengar on 2009-10-19
> **kaivalagi said:**
> Running this:
```
ls /usr/bin/conkyGoogleCalendar
```

Should give you this:
```
-rwxr-xr-x 1 root root 133 2008-09-08 23:16 /usr/bin/conkyGoogleCalendar
```

That's the main bin based exec file for kick of things with the python script...

If you look up the conkygooglecalendar in Synaptic and right click and go to the installed files tab, you should see this following listed:

```
/.
/usr
/usr/share
/usr/share/conkygooglecalendar
/usr/share/conkygooglecalendar/example
/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template
/usr/share/conkygooglecalendar/example/conkyrc
/usr/share/conkygooglecalendar/conkyGoogleCalendar.py
/usr/share/pyshared-data
/usr/share/pyshared-data/conkygooglecalendar
/usr/share/doc
/usr/share/doc/conkygooglecalendar
/usr/share/doc/conkygooglecalendar/AUTHORS
/usr/share/doc/conkygooglecalendar/changelog.gz
/usr/share/doc/conkygooglecalendar/README.gz
/usr/share/doc/conkygooglecalendar/copyright
/usr/share/pyshared
/usr/share/pyshared/conkygooglecalendar-2.06.egg-info
/usr/bin
/usr/bin/conkyGoogleCalendar

```

If all of that matches up then I suggest you just run the following (to remove and reinstall it):

```
sudo apt-get remove conkygooglecalendar && sudo apt-get autoclean && sudo apt-get install conkygooglecalendar
```

Hope that helps

Everything matched up and I reinstalled again, but with the same result.  It won't update.

---

### Post by kaivalagi on 2009-10-19
> **idigchess said:**
> Everything matched up and I reinstalled again, but with the same result.  It won't update.

Okay, lets try running the script this way instead:

```
python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py -n -l 10 -d 3 --timeformat="%l:%M %P" -u xxxxxxxxxx -p xxxxxxxxxxxxxxxxxxxx -v
```

The -v gives verbose output...

You should get something like this before the event output:

```
*** INITIAL OPTIONS:
    username: **************
    password: **************
    daysahead: 3
    startdate: None
    enddate: None
    allevents: False
    wordsearch: None
    limit: 10
    template: None
    dateformat: None
    indent: 0
    nowho: True
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching future event data, for the next 3 days...
INFO: Processing output...
```

---

### Post by josephellengar on 2009-10-19
> **kaivalagi said:**
> Okay, lets try running the script this way instead:

```
python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py -n -l 10 -d 3 --timeformat="%l:%M %P" -u xxxxxxxxxx -p xxxxxxxxxxxxxxxxxxxx -v
```

The -v gives verbose output...

You should get something like this before the event output:

```
*** INITIAL OPTIONS:
    username: **************
    password: **************
    daysahead: 3
    startdate: None
    enddate: None
    allevents: False
    wordsearch: None
    limit: 10
    template: None
    dateformat: None
    indent: 0
    nowho: True
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching future event data, for the next 3 days...
INFO: Processing output...
```

Thanks.  I figured it out after I did the verbose output.  It didn't like a special character that I had in my password. ](*,)  LOL.  What trouble.  Thanks!

---

### Post by kaivalagi on 2009-10-19
> **idigchess said:**
> Thanks.  I figured it out after I did the verbose output.  It didn't like a special character that I had in my password. ](*,)  LOL.  What trouble.  Thanks!

Can you tell me what character?

---

### Post by josephellengar on 2009-10-19
> **kaivalagi said:**
> Can you tell me what character?

Just a parentheses.  I had to add the forward slash before it.

---

### Post by omnisciencedoggy on 2009-10-22
> **kaivalagi said:**
> This must mean the google calendar api start and stop dates are UTC i.e. expect GMT+0...not sure if I can get a fix out for some time (family hols coming up)

Thanks again for a great app!  Has there been any headway made on this issue?

---

### Post by kaivalagi on 2009-10-23
> **omnisciencedoggy said:**
> Thanks again for a great app!  Has there been any headway made on this issue?

Thanks for reminding me, to be honest work is quite hectic since my hols (I need another one!) and time has been tight...I'll try to take a look at the weekend if I can

---

### Post by josephellengar on 2009-10-27
I'm suddenly getting errors again and my events aren't showing up.  This is my terminal output:

```

ERROR: getFutureEvents:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 344, in getFutureEvents
    feed = self.cal_client.CalendarQuery(query)
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 115, in CalendarQuery
    result = self.Query(query.ToUri())
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 111, in Query
    result = self.Get(uri)
  File "/var/lib/python-support/python2.5/gdata/service.py", line 556, in Get
    'reason': server_response.reason, 'body': result_body}
RequestError: {'status': 400, 'body': 'Invalid UserId en.australian', 'reason': 'Bad Request'}

```

---

### Post by kaivalagi on 2009-10-28
> **idigchess said:**
> I'm suddenly getting errors again and my events aren't showing up.  This is my terminal output:

```

ERROR: getFutureEvents:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 344, in getFutureEvents
    feed = self.cal_client.CalendarQuery(query)
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 115, in CalendarQuery
    result = self.Query(query.ToUri())
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 111, in Query
    result = self.Get(uri)
  File "/var/lib/python-support/python2.5/gdata/service.py", line 556, in Get
    'reason': server_response.reason, 'body': result_body}
RequestError: {'status': 400, 'body': 'Invalid UserId en.australian', 'reason': 'Bad Request'}

```

Have you added a public calendar? Sometimes public calendars break the script and need to be excluded in the options

---

### Post by josephellengar on 2009-10-28
> **kaivalagi said:**
> Have you added a public calendar? Sometimes public calendars break the script and need to be excluded in the options

Nope.  Still all private.  It just stopped working one day.  I am connected to the internet and my username/password are both accurate.

---

### Post by kaivalagi on 2009-10-28
> **idigchess said:**
> Nope.  Still all private.  It just stopped working one day.  I am connected to the internet and my username/password are both accurate.

Then I have absolutely no idea, I've not changed the package at all recently, and if your settings and calendar are unchanged then there is no reason for this...

Are you running Karmic RC? That's all I can think of now...unready gdata package maybe???

---

### Post by josephellengar on 2009-10-28
> **kaivalagi said:**
> Then I have absolutely no idea, I've not changed the package at all recently, and if your settings and calendar are unchanged then there is no reason for this...

Are you running Karmic RC? That's all I can think of now...unready gdata package maybe???

No, I'm still on good stable, reliable Ibex :)

---

### Post by kaivalagi on 2009-10-28
> **idigchess said:**
> No, I'm still on good stable, reliable Ibex :)

I think I'm going to switch to Arch...I made the fatal mistake of upgrading to Karmic RC due to it working fine on a laptop I did a fresh install on...it screwed my previously Jaunty install up and now I think a rolling release distro like Arch is a better option...for me...

This post was submitted in Windows 7...I am actually quite liking it *kaivalagi ducks*. And yes I have an excuse, I develop for windows in my day job - I still not found that ever elusive open source development role, that pays anyway.

It might mean all these conky scripts will not be supported through packages anymore, instead they'll be tarball based...still debating with myself :)

As for your issue with the script I am stumped...

---

### Post by josephellengar on 2009-10-28
> **kaivalagi said:**
> I think I'm going to switch to Arch...I made the fatal mistake of upgrading to Karmic RC due to it working fine on a laptop I did a fresh install on...it screwed my previously Jaunty install up and now I think a rolling release distro like Arch is a better option...for me...

It might mean all these conky scripts will not be supported through packages anymore, instead they'll be tarball based...still debating with myself :)

As for your issue with the script I am stumped...

Thanks for your help.  Maybe it'll work when I do the fresh koala install next week or so on my new computer.

---

### Post by EmeraldOZ on 2009-10-29
Hi Kaivalagi, I know the main focus of this thread has been your google calendar script but I'd just like to revisit the google reader script you wrote way back in the first few pages. I've found it very useful but a couple weeks ago it stopped working. This is what I get when I run it in a terminal.

> username: ****
password: ****
datatype: UI
verbose: True
Traceback (most recent call last):
  File ".scripts/conkyGoogleReader.py", line 124, in <module>
    unreadfeedscount, unreaditemtotalcount, feeds = greader.getUnreadItems()
  File ".scripts/conkyGoogleReader.py", line 63, in getUnreadItems
    usock = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 124, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 395, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 508, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 433, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 367, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 516, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 401: Unauthorized

My username and password are still the same but I'm getting an Unauthorized error. Any idea what's wrong? Thanks.

---

### Post by kaivalagi on 2009-10-30
> **EmeraldOZ said:**
> Hi Kaivalagi, I know the main focus of this thread has been your google calendar script but I'd just like to revisit the google reader script you wrote way back in the first few pages. I've found it very useful but a couple weeks ago it stopped working. This is what I get when I run it in a terminal.



My username and password are still the same but I'm getting an Unauthorized error. Any idea what's wrong? Thanks.

Unfortunately I am not running Ubuntu now, I have jumped ship to ArchLinux because I got fed up with issues on upgrading versions of Ubuntu and wanted a rolling release style linux.

I am in the process of getting my system setup so can't help for now.

It may be some time before I can take a look...

---

### Post by josephellengar on 2009-10-30
> **EmeraldOZ said:**
> Hi Kaivalagi, I know the main focus of this thread has been your google calendar script but I'd just like to revisit the google reader script you wrote way back in the first few pages. I've found it very useful but a couple weeks ago it stopped working. This is what I get when I run it in a terminal.


My username and password are still the same but I'm getting an Unauthorized error. Any idea what's wrong? Thanks.


I'm thinking that google might have changed the way that th user data is accessed if this broke at the same time my google calendar did.  I wonder if anybody else had the same problem.

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by EmeraldOZ on 2009-11-02
Welcome to Arch. That's actually what I use, I just came here to get that conky Google Reader script. Enjoy setting up your system and thanks for putting the updating of your scripts onto your To Do list.

---

### Post by omnisciencedoggy on 2009-11-02
> **kaivalagi said:**
> This must mean the google calendar api start and stop dates are UTC i.e. expect GMT+0...not sure if I can get a fix out for some time (family hols coming up)

Thanks again for the script.  I was wondering if there was some quick tweak I could do to the conkyGoogleCalendar.py file make it work for my time zone (GMT -6:00) so I can have it working on my computer while I wait for your full update?  Thanks again for your help and for sharing your script!

I've attached an image to show you what I'm going for.  The google calendar script is on the left.  All of the events should be under the "tomorrow" section, with none in the "day after tomorrow" section.  

[[IMG]http://img524.imageshack.us/img524/7248/screenshot1cd.th.png[/IMG]](http://img524.imageshack.us/i/screenshot1cd.png/)

---

### Post by kaivalagi on 2009-11-03
> **omnisciencedoggy said:**
> Thanks again for the script.  I was wondering if there was some quick tweak I could do to the conkyGoogleCalendar.py file make it work for my time zone (GMT -6:00) so I can have it working on my computer while I wait for your full update?  Thanks again for your help and for sharing your script!

I've attached an image to show you what I'm going for.  The google calendar script is on the left.  All of the events should be under the "tomorrow" section, with none in the "day after tomorrow" section.  

[[IMG]http://img524.imageshack.us/img524/7248/screenshot1cd.th.png[/IMG]](http://img524.imageshack.us/i/screenshot1cd.png/)

A quick solution would be to mess with the getDateFromWhen function, you could take 6 hours off the whendatetime variable before it is returned. so all datetimes output are adjusted how you want. I am suffering from flu right now so can't help much I'm afraid,, but if you take a look at the timedelta functions in python they should be all you need...start here: [http://docs.python.org/index.html](http://docs.python.org/index.html)

---

### Post by omnisciencedoggy on 2009-11-03
> **kaivalagi said:**
> A quick solution would be to mess with the getDateFromWhen function, you could take 6 hours off the whendatetime variable before it is returned. so all datetimes output are adjusted how you want. I am suffering from flu right now so can't help much I'm afraid,, but if you take a look at the timedelta functions in python they should be all you need...start here: [http://docs.python.org/index.html](http://docs.python.org/index.html)

Thanks again!  Get well soon.

---

### Post by Lockheed on 2009-11-24
With this script, can you only view the calendar events, or can you actually add/modify them?

---

### Post by josephellengar on 2009-11-24
> **Lockheed said:**
> With this script, can you only view the calendar events, or can you actually add/modify them?

View only.  Conky is non-interactive.

---

### Post by Lockheed on 2009-11-25
Fair enough. I just triead Rainlendar and it can do both but it's not free.

---

### Post by kaivalagi on 2009-11-25
> **Lockheed said:**
> Fair enough. I just triead Rainlendar and it can do both but it's not free.

If you want an editable google calendar you could always load the calendar url on the desktop using my gtk-desktop-info app (would be the whole page though). Link in my sig...

Just a thought

---

### Post by fooey on 2009-12-12
**conkygooglereader** doesn't seem to be working anymore. i know the original dev moved onto another distro, but does anyone know if it's still supposed to work?

```
conkyGoogleReader --username=myusername --password=mypw

Traceback (most recent call last):
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 228, in <module>
    main()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 225, in main
    greader.writeOutput()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 92, in writeOutput
    unreadfeedscount, unreaditemtotalcount, feeds = self.getUnreadItems()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 133, in getUnreadItems
    usock = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 124, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 395, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 508, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 433, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 367, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 516, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 401: Unauthorized
```

---

### Post by Bruce M. on 2009-12-12
> **fooey said:**
> **conkygooglereader** doesn't seem to be working anymore. i know the original dev moved onto another distro, but does anyone know if it's still supposed to work?

K's is still supporting his apps, just no more **.deb** files.  Also things changed with Ubuntu 9.10 and created a few problems.

He'll be here to help.  Have faith.  :)
I don't use this one so can't help.

Bruce

---

### Post by kaivalagi on 2009-12-12
> **fooey said:**
> **conkygooglereader** doesn't seem to be working anymore. i know the original dev moved onto another distro, but does anyone know if it's still supposed to work?

```
conkyGoogleReader --username=myusername --password=mypw

Traceback (most recent call last):
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 228, in <module>
...
  File "/usr/lib/python2.6/urllib2.py", line 516, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 401: Unauthorized
```

As Bruce has said I am still about these parts, just not creating package updates...I can however provide file updates with simple instructions until I figure out a new install method for all distros...

I get the same error, and I guess it will need looking into it at some point. To be honest this script isn't used by many, me included these days - it doesn't have it's own thread in the site for a start. I don't have much free time right now, because of my current work and other hobbies so I can't give you a time frame for any maintenance.

I will take a look at some point though...

---

### Post by fooey on 2009-12-12
Doh. I read further on up on this page of this thread. someone else had this problem. guess it's just kinda dead. don't  blame him.
;)

---

### Post by kaivalagi on 2009-12-14
> **EmeraldOZ said:**
> Hi Kaivalagi, I know the main focus of this thread has been your google calendar script but I'd just like to revisit the google reader script you wrote way back in the first few pages. I've found it very useful but a couple weeks ago it stopped working. This is what I get when I run it in a terminal.

My username and password are still the same but I'm getting an Unauthorized error. Any idea what's wrong? Thanks.

> **rossholley said:**
> I'm thinking that google might have changed the way that th user data is accessed if this broke at the same time my google calendar did.  I wonder if anybody else had the same problem.

> **fooey said:**
> Doh. I read further on up on this page of this thread. someone else had this problem. guess it's just kinda dead. don't  blame him.
;)

Right, I have fixed the conkyGoogleReader script, but cannot update the package as I do not have the necessary tools. I have checked in the latest edition of the script and have it workin for Arch based AUR installs but for you guys I think you'll just have to replace the script file for now - steps as follows:

[LIST=1]
[*]Copy the attachment to /tmp/conkyGoogleReader.py
[*]run this to copy it in over the top of the old one "sudo cp /tmp/conkyGoogleReader.py /usr/share/conkygooglereader"
[*]Job done, have fun :)
[/LIST]

I had to rewrite the authentication mechanism as google changed how it worked...

Any issues let me know, I'm sure you will anyway ;)

Also I'd like to point out that this script is experimental unlike my other conky scripts and as such don't expect it to work as time goes on...google have not published a proper API for google reader so the script only works by sheer luck really.

---

### Post by KenJean on 2009-12-19
Just want to say that you are the greatest. Been waiting for this new Google Reader script.

Many, many thanks.

-KJ :)

---

### Post by kaivalagi on 2009-12-20
> **KenJean said:**
> Just want to say that you are the greatest. Been waiting for this new Google Reader script.

Many, many thanks.

-KJ :)

Don't know about the greatest but I'm glad the script is useful again. I didn't know that in was in use by so many...

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by walter s. on 2010-01-23
thanks for the google reader update.

i was looking thorugh the files but i couldn't find any hint for my problem.
there are only 4 (or rather 3 and a half) feeds listet with their amount of unread entrys.

the fourth one isnt completly but cutted off somewhere in the middle of the URL

would appreciate any hintes. 
thanks in advance

---

### Post by kaivalagi on 2010-01-23
> **walter s. said:**
> thanks for the google reader update.

i was looking thorugh the files but i couldn't find any hint for my problem.
there are only 4 (or rather 3 and a half) feeds listet with their amount of unread entrys.

the fourth one isnt completly but cutted off somewhere in the middle of the URL

would appreciate any hintes. 
thanks in advance

Try increasing the text buffer size, try adding this after the TEXT line in your conkyrc:

```
text_buffer_size 2048
```

---

### Post by walter s. on 2010-01-23
just wanted t apologize as i've found out that it was the text buffer.

thanks :)

---

### Post by amandkumar on 2010-01-23
I want the google calendar in my computer. But little bit confused up on how to proceed.

---

### Post by kaivalagi on 2010-01-24
> **walter s. said:**
> just wanted t apologize as i've found out that it was the text buffer.

thanks :)

No worries

---

### Post by kaivalagi on 2010-01-24
> **amandkumar said:**
> I want the google calendar in my computer. But little bit confused up on how to proceed.

I would suggest:

[LIST=1]
[*]Get your head around conky and all the options it has available, try visiting [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)
[*]Read through the first post of this thread fully, there are installation instructions along with lots of help on setup as well as pointers to the example files included in the package that will help get you started
[*]If still in doubt, have a read over at [http://conky.linux-hardcore.com](http://conky.linux-hardcore.com)
[*]Once you have something up and running and if you still have issues then post what you have written and we can see what is up, but please read through everything first and try to figure out problems for yourself first
[/LIST]

Please don't expect anyone to provide you with what you want, it is up to you to figure out how it works (with a lot of help from docs/guides). You need to know how it all works to be able to use it. That being said, there are loads of examples to be found out there which should provide what you need

Hope that helps

---

### Post by Technoviking on 2010-06-17
I'm getting the following errors with this script. Using Ubuntu 10.04.

```
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 157, in __init__
    self.getCalendarList()
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 191, in getCalendarList
    cal.username    = urllib.unquote(match.group(1))
AttributeError: 'NoneType' object has no attribute 'group'
```

No Events...

Calling the script with the following variables

```
conkyGoogleCalendar --username=***** --password=***** --daysahead=7 --limit=3 --nowho
```

---

### Post by michote on 2010-07-22
Hi 
your script works fine for me without a template, but if I use one I get a UnicodeDecodeError with german umlauts. (I have added the override_utf8_locale yes):

```
~$ python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py -u ***** -p ***** -d 3 -l 3 -i 5 -f "%a" -F "%H:%M" -m 20 -n
      Title: Gespräch Carsten
      Start Time: Do 18:00
      End Time: Do 20:00
      Location: Carsten

      Title: Restmüll- Tonnen und Container 14-täglich
      Start Time: Fr
      End Time: Sa
      Location: Erzhausen

      Title: voraussichtlicher TERMIN
      Start Time: Fr
      End Time: Sa

~$ python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py -u ***** -p ***** -d 3 -l 3 -i 5 -f "%a" -F "%H:%M" -m 20 -t /home/micha/.ConkyWizardTheme/scripts/conkyGoogleCalendar.template -n
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 374, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 21: ordinal not in range(128)


ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 374, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 5: ordinal not in range(128)


Fr
Sa
voraussichtlicher TERMIN
```

any help or ideas?

---

### Post by kaivalagi on 2010-07-22
I've tried to reproduce after fixing technoviking's issue and see no more problems...but as I haven't got your template I can't be certain your problems will have been sorted out too.

Could you replace /usr/share/conkyGoogleCalendar/conkyGoogleCalendar.py with the one attachedand feedback what happens? If it's still the same then could you post your template contents so I can reproduce properly please?

@Technoviking, sorry it's taken so long, I have been somewhat busy of late, for now if you want a working script replace with the py attached, once I have a working script fixing both recent problems posted I'll arrange a new package to be released

Cheers

---

### Post by michote on 2010-07-23
Thanks for your quick reply!
Using the new version of the script I get the following error:
```
micha@michote:~$ python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py -u ***** -p ***** -l 3
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 119, in __init__
    self.getCalendarList()
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 153, in getCalendarList[starttime]
[endtime]
[title]
Ort: [location]
    cal.username    = urllib.unquote(match.group(1))
AttributeError: 'NoneType' object has no attribute 'group'

No Events...

```

my template is very simple, just placeholders for now:
```
[starttime]
[endtime]
[title]
Ort: [location]
```

---

### Post by kaivalagi on 2010-07-23
mmmmm, looks like the fix that is required for Technoviking and myself isn't required for you....the error you are now getting is the same one I was...it's a http verses https issue I may need to get clever with regex for.

I might be able to take a look at some point over the next few days but no promises

To be honest I think the original issue you were having relates to python and the way it handles unicode text (accented chars etc outside of the ascii char set)...I may need to go back to the drawing board and look at a better way to handle unicode, if there is one.

Anything I figure out I'll post here, just not sure when...

Cheers

---

### Post by xjgnsdof on 2010-08-03
Conky doesn't show all my GCal events for today, but it shows all the events on Wednesday and Thursday. I just want it to show all of today's events.

---

### Post by kaivalagi on 2010-08-03
> **elgilicious said:**
> Conky doesn't show all my GCal events for today, but it shows all the events on Wednesday and Thursday. I just want it to show all of today's events.

Post your conkyrc and template if you use one

---

### Post by xjgnsdof on 2010-08-03
.conkyGoogleCalendar.template:

```
${color3}${font Arial:bold}Event:$font ${color1}[title]
${color3}${font Arial:bold}Start:$font ${color1}[starttime]
${color3}${font Arial:bold}End:$font ${color1}[endtime]
${color3}${font Arial:bold}Description:$font ${color1}[description]
${color3}${font Arial:bold}Place:$font ${color1}[location]

```

.conkyrc:

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont arial:size=11:bold

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
#border_margin 4
#window.border_inner_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none
#alignment middle_left
#alignment middle_right
alignment top_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

text_buffer_size 1100
#text_buffer_size 10000
maximum_width 300

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

color1 white
color3 5A7593

TEXT
${color #5A7593} ${font Arial:bold:size=12}SCHEDULE$font ${hr 2}$color
${execpi 30 conkyGoogleCalendar --username=XXXXXXXXX --password=XXXXXXX --template=/home/emones/.conkyGoogleCalendar.template}
```

---

### Post by kaivalagi on 2010-08-03
I think you may need the fix attached in post #335, just a few posts back on this page or if you're lazy [here]("http://ubuntuforums.org/showpost.php?p=9623653&postcount=335")

You'll need to replace this file with what's in the tarball: /usr/share/conkygooglecalendar/conkyGoogleCalendar.py

Hope that helps

---

### Post by xjgnsdof on 2010-08-03
Now, no events appear.

---

### Post by pastorjack on 2010-08-17
Hi,
I just downloaded your script, and it looks like exactly what I want.
Thank you so much.

I am however having one problem,
I am using a template to limit the output to just title and start date, 
the info shows up in conky fine, but it includes the ${color} tag.

I have set default values for ${color1} etc. which are recognized by my other
conky script for gmail.

just wondering if you might have some insight on why these variables dont get 
passed on to the script.

any help at all would be greatly appreciated,

--j

---

### Post by kaivalagi on 2010-08-18
Are you calling the script using exec**p**i? It's needed to parse the conky variables from the template

---

### Post by kaivalagi on 2010-08-18
> **brainbechtol said:**
> thansk for the prompt updates
Sarcasm? I've left it for a while because I do have a life...

> **elgilicious said:**
> Now, no events appear.

Stopped working after the latest update? If you are more helpful in your posts I can be too...

I know that most people had problems with gcal as they changed the feed urls returned by gdata libraries from http to https, but maybe some are left with the former?

edit: I've updated the script (attached) to allow both http and https feed urls, so it should now work for everyone...please confirm

---

### Post by pastorjack on 2010-08-18
> Are you calling the script using exec**p**i? It's needed to parse the conky variables from the template 	

This fixes it.  Now this script is the bees knees.  Thanks so much for making this script and keeping it up so well.

I am in your debt.

--j

---

### Post by kaivalagi on 2010-08-18
> **pastorjack said:**
> This fixes it.  Now this script is the bees knees.  Thanks so much for making this script and keeping it up so well.

I am in your debt.

--j

Glad you find it useful, I try ;)

---

### Post by kaivalagi on 2010-08-18
**[COLOR="DarkOrange"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Updated to handle both http and https based feed urls as google changed the gdata libraries and what they return (for some!)
[/LIST]

Changes can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.08_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.08_source.changes)

The new apt package should be available soon

Cheers

---

### Post by Izobalax on 2010-08-29
Hi kaivalagi,

These are some absolutely kick *** scripts, thank you so much. I'm trying desperately to get the conkyGoogleReader script running, but I'm not having much luck.

My conky config:

```
# Conky configuration
# Edited by Izobalax 2009

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 205 47
maximum_width 205

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		desktop
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 8	
gap_y 63

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${image /home/izo/Pictures/Desktop_Modding/Conky/Litestyle/Gmail/litestyle-conky-gmail.png
 -p 0,0 -s 205x47}${offset 5}${voffset 2}${color #E0E0E0}${font Swis721 Cn BT:size=10}Google Reader
${offset 5}${voffset 5}${color #E0E0E0}${font Swis721 Cn BT:size=10}You have 0${execi 600 conkyGoogleReader --username=MYUSERNAME9@gmail.com --password=MYPASSWORD} unread item(s)
```

If in the terminal, and I run the command:

```
conkyGoogleReader -u=MYUSERNAME9@gmail.com -p=MYPASSWORD
```

I get this:

```
Traceback (most recent call last):
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 238, in <module>
    main()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 235, in main
    greader.writeOutput()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 76, in writeOutput
    auth_header = self.getAuth()
  File "/usr/share/conkygooglereader/conkyGoogleReader.py", line 129, in getAuth
    auth_resp = urllib2.urlopen(auth_req)
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 403: Forbidden
```

What am I doing wrong?

/izo\

---

### Post by kaivalagi on 2010-08-29
> **Izobalax said:**
> Hi kaivalagi,

These are some absolutely kick *** scripts, thank you so much. I'm trying desperately to get the conkyGoogleReader script running, but I'm not having much luck.

...

What am I doing wrong?

/izo\

There is a reason there is no thread for conkyGoogleReader, it is experimental and unsupported. I just tried running it after many months of not using it and google have obviously changed things, I get a 401 error...

I'll have a quick look and debug the script but am not sure if you'll have a working script by the end of it...

edit: I am not alone in issues bringing feed info back, the auth mechanism isn't working with cookies or an authorization header...yet the url works in a browser. Sorry mate, it's not happening...

---

### Post by KenJean on 2010-08-29
Just to let you know, I too, have been using your Google Reader script.

As I figured you are a busy person, when it "broke" last month I didn't post about the problem as I was sure you'd get to it when you had time.

Sorry to hear that it's not working, but thanks for trying.

-KJ

---

### Post by kaivalagi on 2010-08-29
> **KenJean said:**
> Just to let you know, I too, have been using your Google Reader script.

As I figured you are a busy person, when it "broke" last month I didn't post about the problem as I was sure you'd get to it when you had time.

Sorry to hear that it's not working, but thanks for trying.

-KJ

I've bookmarked the place where questions are being raised, and will keep an eye on it from time to time. It's in the comments at the end of this page: [http://code.google.com/p/pyrfeed/wiki/GoogleReaderAPI](http://code.google.com/p/pyrfeed/wiki/GoogleReaderAPI)

If you see something of promise make sure I know!

---

### Post by kaivalagi on 2010-08-29
r.e. conkyGoogleReader

I have fixed the google reader script now :)

I've attached the .py file and expect the package to have an update soon

Details of the fix (if you're interested) can be found in my comments in the above linked page

---

### Post by KenJean on 2010-08-29
You da man!!!!!

We shall make you Pope!!! (I shall also donate.)

Many, many thanks.

-KJ

---

### Post by kaivalagi on 2010-08-29
> **KenJean said:**
> You da man!!!!!
We shall make you Pope!!! (I shall also donate.)
Many, many thanks.
-KJ

Not sure the world would be a better place with me as pope lol, me being agnostic and all :)

Thanks for the donation, gratefully received :D

edit: Arch AUR and Ubuntu packages are now available for update

---

### Post by Izobalax on 2010-08-29
You, sir, are a legend. Updating now. 

/izo\

---

### Post by kaivalagi on 2010-09-03
**[COLOR="Red"]FAO: conkyGoogleReader script users[/COLOR]**

I've added more functionality to the conky google reader script.

The script can now output for the following placeholders when in a new summary mode: [totalfeedscount], [unreadfeedscount], [unreadfeeditemscount].

There is default output for --summaryouput/-S but this can be modified via a --summarytemplate/-s option.

An example of this output is:

```
1451 unread feed items, 10/112 feeds have unread content.
```

Full -h output for the script is now:

```
Usage: conkyGoogleReader [options]
Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        username to login with
  -p PASSWORD, --password=PASSWORD
                        Password to login with
  -t FILE, --template=FILE
                        Template file determining the format for each rss feed
                        summary. Use the following placeholders:
                        [unreadcount], [name], [url]
[B]  -s FILE, --summarytemplate=FILE
                        Template file determining the format for summary
                        output. Use the following placeholders:
                        [totalfeedscount], [unreadfeedscount],
                        [unreadfeeditemscount]
  -S, --summaryoutput   Request summary output rather than each feeds details[/B]
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

The new version of the script should appear via apt soon :D
changes on launchpad: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.04_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.04_source.changes)

I really ought to create a new thread for this script!

---

### Post by Izobalax on 2010-09-03
That is superb work, just what I was looking for!

---

### Post by etescartz on 2010-09-03
This is a happy day for me.Cannot wait to try this... Thank you! My conky will now be one step closer to perfection...

---

### Post by kaivalagi on 2010-09-03
Glad to hear it!

I've created a thread for the conkyGoogleReader script now, you can find it here: [http://ubuntuforums.org/showthread.php?p=9800463](http://ubuntuforums.org/showthread.php?p=9800463)

I suggest if you have any questions/suggestions for the script post them there.

Cheers

---

### Post by Wangsta on 2010-09-05
So, this thread hasn't been updated recently, but I was wondering if there was any way that I could have the time BEFORE the date?

Such as: 3:00pm Mon 7

thanks!

---

### Post by alanwalterthomas on 2010-09-06
Can conkyGoogleCalendar, or anthing else I could possibly hook into conky, access Google Tasks? So far I've only been able to get calendar events to appear, but I also use google tasks which can appear on the online calendar as well.
Thanks,

---

### Post by alanwalterthomas on 2010-09-14
Bump, why do threads keep dying as soon as I ask a question...??
Is there any way I can get my soonest-upcoming google tasks to show up in conky? (as opposed to google calendar events?)

---

### Post by kaivalagi on 2010-09-15
> **Wangsta said:**
> So, this thread hasn't been updated recently, but I was wondering if there was any way that I could have the time BEFORE the date?

Such as: 3:00pm Mon 7

thanks!

Just mess about with these 2 options:
```
  -f "DATEFORMAT", --dateformat="DATEFORMAT"
                        If used this overrides the default date formatting.
                        The values to use are standard formatting strings e.g.
                        Weekday=%a, Day=%d, Month=%m, Year=%y. For an output
                        like "Thu 15/10/2008" you would require
                        --dateformat="%a %d/%m/%y", to have no date you would
                        require --dateformat=""
  -F "TIMEFORMAT", --timeformat="TIMEFORMAT"
                        If used this overrides the default time formatting.
                        The values to use are standard formatting strings e.g.
                        Hours (12hr)=%l, Hours (24hr)=%H, Minutes=%M,
                        Seconds=%S, AM/PM=%P. For an output like "05:22 PM"
                        you would require --timeformat="%l:%M %P",
                        --timeformat="" is not supported, default locale
                        settings are used

```

---

### Post by kaivalagi on 2010-09-15
> **alanwalterthomas said:**
> Bump, why do threads keep dying as soon as I ask a question...??
Is there any way I can get my soonest-upcoming google tasks to show up in conky? (as opposed to google calendar events?)

Don't know of anything sorry

---

### Post by Goombie on 2010-09-22
I'm loving your calendar script. It's something I've been looking for - almost. :)
Is there a way to modify the script so that the output is all on one line?
That is, instead of ```

Event one
Event two
Event three
etc

```
as output, I get ```
 Event one, event two, etc 
``` instead when I run the script.

I want to fit a scrolling feed of my gcal events into one line on Conky. Thanks for any help!

---

### Post by kaivalagi on 2010-09-22
> **Goombie said:**
> I'm loving your calendar script. It's something I've been looking for - almost. :)
Is there a way to modify the script so that the output is all on one line?
That is, instead of ```

Event one
Event two
Event three
etc

```
as output, I get ```
 Event one, event two, etc 
``` instead when I run the script.

I want to fit a scrolling feed of my gcal events into one line on Conky. Thanks for any help!

The script on its own can't but use sed to replace new line with commas and you should get what you want...e.g.

Execi conkyGoogleCalendar ...options...¦ sed ...options...

Where "¦" is a pipe (on my phone)

---

### Post by ppihus on 2010-10-07
Great script! :)
Though I'm having some problems to which I was unable to find a solution.

Everything works great on regular calendars, but my Google Calendars also include one imported by URL calendar (and that's the most important one). The events from this calendar show up in conky -3 hours.
So when I have "EVENT A" starting at 14:15, conky shows that it starts at 11:15.

What could be the problem? Other calendars work just fine.

Thanks in advance.

---

### Post by kaivalagi on 2010-10-07
mmmm, I had a similar issue in the past because of certain calendar feeds being based in other timezones...I don't think I found a solution. Can you let me know what the public calendars you've added in that have this issue so I can try and reproduce it?

---

### Post by ppihus on 2010-10-07
I sent you a link to the calendar I'm having problems with. Since it's my school's daily schedule, I don't want to post this in public forums.

I myself am located at GMT+2 timezone

---

### Post by kaivalagi on 2010-10-07
> **ppihus said:**
> I sent you a link to the calendar I'm having problems with. Since it's my school's daily schedule, I don't want to post this in public forums.

I myself am located at GMT+2 timezone

So the school's located at GMT-1?

I see the first events of the day showing as 8:15am and I am in the UK (GMT+0), does that tie in with the equivalent to you? i.e. Should be 9:15am?

---

### Post by ppihus on 2010-10-07
> **kaivalagi said:**
> So the school's located at GMT-1?

I see the first events of the day showing as 8:15am and I am in the UK (GMT+0), does that tie in with the equivalent to you? i.e. Should be 9:15am?
My school is  also located at GMT+2. The .ics file has time and dates exactly as they should be in my timezone.

For example:
```
"SUMMARY:Programmeerimine C-keeles MTAT.03.219 praktikum"
```This is supposed to start at 12:15 and end at 14:00. The .ics also has 121500 and 140000. But conkyGoogleCalendar shows this as 9:15-11:00

Do you have any idea why is this so?

---

### Post by kaivalagi on 2010-10-07
It's showing for me as 10:15 - 12:00 for me i.e. as the right time for where I am (GMT+0)...10:15am where I am is the same point in time as 12:15 in GMT+2

In my mind I'd say it's working just fine for me but I can't make sense of why it differs for you if both the school and you are in GMT+2...

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.09_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.09_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.10_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglecalendar_2.10_source.changes)

The apt packages should be available soon

---

### Post by KenJean on 2010-11-25
I hope this isn't just me:

Something appears to be broken with the -f switch.

Heretofore -f "%a %m-%d" produced the output "Tue 11-30". Now it only produces "Tue"

It appears that the space in the format string is causing the truncation, because -f "%a%m-%d" will produce "Tue11-30"

Any ideas?

-KJ

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by donniezazen on 2011-01-12
Thanks for the tutorial and your work. I am kind of lost. What do i do after i have installed the script?

---

### Post by kaivalagi on 2011-01-12
> **soham_1207 said:**
> Thanks for the tutorial and your work. I am kind of lost. What do i do after i have installed the script?

Have a look at the example files found here: /usr/share/conkygooglecalendar/example/

They wont work as they are as they need to be populated with a proper gmail account username and password...

If you copy them to a folder somewhere in your home drive and then edit them to hold bearing in mind some of the contents need changing for the right paths etc

If you're stuck with conky in general take a look at the conky pitstop (link below in my sig)

Hope that helps

---

### Post by robosushi on 2011-01-18
First of all, thanks so much for developing this script! It's really great.

Now, I've got a timezone-related problem with the script. All of the events are being displayed in the GMT-0 timezone, but I'm in GMT-8. Any advice? I'm running Maverick and have the most recent version of the script installed (just got it a few days ago).

Thanks!

---

### Post by robosushi on 2011-01-18
Sorry, double post.

---

### Post by kaivalagi on 2011-01-18
> **robosushi said:**
> First of all, thanks so much for developing this script! It's really great.

Now, I've got a timezone-related problem with the script. All of the events are being displayed in the GMT-0 timezone, but I'm in GMT-8. Any advice? I'm running Maverick and have the most recent version of the script installed (just got it a few days ago).

Thanks!

mmmmm, this has cropped up before with no solution, it seems that google's gdata api doesn't support time zones well with some calendars...

Is it all your calendars or just one? If you only have 1 calendar can I suggest you create another one to test with also.

---

### Post by robosushi on 2011-01-18
> **kaivalagi said:**
> mmmmm, this has cropped up before with no solution, it seems that google's gdata api doesn't support time zones well with some calendars...

Is it all your calendars or just one? If you only have 1 calendar can I suggest you create another one to test with also.
Interesting... I hadn't thought of that. I do have 3 different calendars that I pull from Google Calendar, and I'm currently only seeing events from one of them. I threw in a fake event for each of the other two calendars, and they both work fine. So, it's only one of my calendars that has this problem. Any ideas?

---

### Post by kaivalagi on 2011-01-18
Nope, like I said no solution for calendars that fail to work in non GMT...and as I am in GMT it is kinda awkward for me to test well.

If you find anything of interest out keep me in the loop, if there is a solution I'll get to work on it I just dont know of one at the mo...

---

### Post by mahatman2 on 2011-01-19
I have this same problem, if it's of any interest. I am running Maverick in GMT-5:00 (Eastern Time US) and otherwise the script works great. It seems like you're not at fault here anyway. Here's to Google fixing it and thanks to your contribution!

---

### Post by mahatman2 on 2011-01-19
I have this same problem, if it's of any interest. I am running Maverick in GMT-5:00 (Eastern Time US) and otherwise the script works great. It seems like you're not at fault here anyway. Here's to Google fixing it and thanks to your contribution!

---

### Post by HippyRandall on 2011-01-23
getting this output in the terminal:


```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 336, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 22: ordinal not in range(128)
```

The calendar appears to be rendering the info properly. Not sure what this is all about

gnight conkyland ;)

---

### Post by kaivalagi on 2011-01-23
> **HippyRandall said:**
> getting this output in the terminal:


```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 336, in getOutputFromTemplate
    output = output.replace("[title]",title)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 22: ordinal not in range(128)
```

The calendar appears to be rendering the info properly. Not sure what this is all about

gnight conkyland ;)

conkyland never sleeps :)

Looks like there is a unicode issue, some accented characters in the output not getting transformed properly maybe...is it a public calendar that's doing this if so can I have the details so I can reproduce the problem?

---

### Post by HippyRandall on 2011-01-23
It is not a public calendar but sent you an invite for it.

> **kaivalagi said:**
> conkyland never sleeps :)

Looks like there is a unicode issue, some accented characters in the output not getting transformed properly maybe...is it a public calendar that's doing this if so can I have the details so I can reproduce the problem?

---

### Post by kaivalagi on 2011-01-23
> **HippyRandall said:**
> It is not a public calendar but sent you an invite for it.

Just ran it with (after editing the name locally for the -r option to match, seems spaces cause issue for calendar naming in this script):
```
conkyGoogleCalendar -u USER -p PASSWORD -d 100 -r hippyrandall --verbose
```

And got no error?:
```
*** INITIAL OPTIONS:
    username: USER
    password: PASSWORD
    daysahead: 100
    startdate: None
    enddate: None
    allevents: False
    wordsearch: None
    limit: 0
    template: None
    dateformat: None
    indent: 0
    nowho: False
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching future event data, for the next 100 days...
INFO: Processing output...
**<Event data outputted as per normal>**

```

What options are you using to see the error?

---

### Post by HippyRandall on 2011-01-23
> **kaivalagi said:**
> Just ran it with (after editing the name locally for the -r option to match, seems spaces cause issue for calendar naming in this script):
```
conkyGoogleCalendar -u USER -p PASSWORD -d 100 -r hippyrandall --verbose
```

And got no error?:
```
*** INITIAL OPTIONS:
    username: USER
    password: PASSWORD
    daysahead: 100
    startdate: None
    enddate: None
    allevents: False
    wordsearch: None
    limit: 0
    template: None
    dateformat: None
    indent: 0
    nowho: False
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Initialising google calendar connection...
INFO: Preparing google calendar list...
INFO: Fetching future event data, for the next 100 days...
INFO: Processing output...
**<Event data outputted as per normal>**

```

What options are you using to see the error?

Here is the call. The template file is just the default, nothing new.

```
${color4}${font Bitstream Vera Sans Mono:size=14}@ ${font Liberation Sans:style=Bold:size=11}Calendar Using Template${font}   ${hr}
${color1}${font}${execpi 600 conkyGoogleCalendar --username=hippyrandall@gmail.com --password=DELETED --daysahead=5 --limit=10  --timeformat="%l:%M %P" --template=/home/hippy/conkyGoogleCalendar.template} 
```

I am also getting this weirdness with the output on my screen(attached screenshot):

---

### Post by kaivalagi on 2011-01-24
> **HippyRandall said:**
> Here is the call. The template file is just the default, nothing new.

```
${color4}${font Bitstream Vera Sans Mono:size=14}@ ${font Liberation Sans:style=Bold:size=11}Calendar Using Template${font}   ${hr}
${color1}${font}${execpi 600 conkyGoogleCalendar --username=hippyrandall@gmail.com --password=DELETED --daysahead=5 --limit=10  --timeformat="%l:%M %P" --template=/home/hippy/conkyGoogleCalendar.template} 
```

I am also getting this weirdness with the output on my screen(attached screenshot):

I used my own template but with the same command line as well as "-r hippyhandall" and it still works fine. The truncating of the output will be because you need to increase the text buffer size....you've forgotten all the tricks ;)

---

### Post by HippyRandall on 2011-01-24
hehe I have indeed forgotten. I increased the buffer and that issue stopped. I still wonder what that error is when just running conky -c ~/.conkyCalendar in a terminal

---

### Post by kaivalagi on 2011-01-24
> **HippyRandall said:**
> I still wonder what that error is when just running conky -c ~/.conkyCalendar in a terminal

I'd say it relates to the event content being outside of the standard ascii character set in some way but for me to test it we need to reproduce consistently...

---

### Post by mockdeep on 2011-01-28
I feel like I ran into this problem way back when and I can't seem to find the post discussing it if there was one.  In short, if there is a space in the name of my calendar it doesn't want to load it:

```
conkyGoogleCalendar -u USERNAME -p PASSWORD --daysahead=7 --limit=10 -r "My Calendar" -f "%A, %B %d" -F ", %l:%M %P" --template=~/Dropbox/scripts/conkyGoogleCalendar.template

```
Says "No Events", even though there are events in my calendar.  On the other hand the same thing works if I select a calendar without a space in the name.  Any ideas?

---

### Post by kaivalagi on 2011-01-28
> **mockdeep said:**
> I feel like I ran into this problem way back when and I can't seem to find the post discussing it if there was one.  In short, if there is a space in the name of my calendar it doesn't want to load it:

```
conkyGoogleCalendar -u USERNAME -p PASSWORD --daysahead=7 --limit=10 -r "My Calendar" -f "%A, %B %d" -F ", %l:%M %P" --template=~/Dropbox/scripts/conkyGoogleCalendar.template

```
Says "No Events", even though there are events in my calendar.  On the other hand the same thing works if I select a calendar without a space in the name.  Any ideas?

Yep, I got around it by renaming the calendar to not have a space in it :)

I didn't think it used to be an issue and have since tried escaping with \, replacing space with %20 and using quotes around the text etc and none of them work...if you figure something out let me know but I suspect renaming is the easiest option!

**edit:** interestingly when running it via python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py if the calendar name (with spaces) is in quotes all is fine...looks like the /usr/bin/conkyGoogleCalendar script is screwing with the quoted argument somehow?????

---

### Post by ScoobyDan on 2011-01-28
I have just installed this script, but when I try to run it (either from within conky, or directly from the CLI) I get the following error message:

```
BadAuthentication: Incorrect username or password
```

I have changed the username and password to my details, and I have double- and triple-checked the details to ensure they are correct.

Could the problem be because I use a special character ($) in my password - is this correctly encoded?

Many thanks,

Daniel

[Edit]
After reading the post above, I tried putting '/' prior to the '$' in my password - and success! Thanks for your help everyone... ;)
[/Edit]

---

### Post by mockdeep on 2011-01-29
> **kaivalagi said:**
> 
**edit:** interestingly when running it via python /usr/share/conkygooglecalendar/conkyGoogleCalendar.py if the calendar name (with spaces) is in quotes all is fine...looks like the /usr/bin/conkyGoogleCalendar script is screwing with the quoted argument somehow?????

Alright, so I've been poking around and the primary result of my research is that bash is a b#&*h when it comes to strings with spaces.  But the secondary result is that I think I found a solution for the problem. Try this:

```

#! /bin/sh

if [ -f /usr/bin/python2 ]; then
	cmd="/usr/bin/python2"
elif [ -f /usr/bin/python2.7 ] ; then
	cmd="/usr/bin/python2.7"
elif [ -f /usr/bin/python2.6 ] ; then
	cmd="/usr/bin/python2.6"
else
	# here's hoping!
	cmd="/usr/bin/python"
fi

exec $cmd "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py" "$@"

```

That does the trick for me.

---

### Post by kaivalagi on 2011-01-29
> **mockdeep said:**
> Alright, so I've been poking around and the primary result of my research is that bash is a b#&*h when it comes to strings with spaces.  But the secondary result is that I think I found a solution for the problem. Try this:

```

#! /bin/sh

if [ -f /usr/bin/python2 ]; then
	cmd="/usr/bin/python2"
elif [ -f /usr/bin/python2.7 ] ; then
	cmd="/usr/bin/python2.7"
elif [ -f /usr/bin/python2.6 ] ; then
	cmd="/usr/bin/python2.6"
else
	# here's hoping!
	cmd="/usr/bin/python"
fi

exec $cmd "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py" "$@"

```

That does the trick for me.

Nice one, thanks.

Slight variation which also works that I shall employ for all the scripts I think, starting with this one:
```

#! /bin/sh
cd /usr/share/conkygooglecalendar/

if [ -f /usr/bin/python2 ]; then
	pythoncmd="/usr/bin/python2"
elif [ -f /usr/bin/python2.7 ] ; then
	pythoncmd="/usr/bin/python2.7"
elif [ -f /usr/bin/python2.6 ] ; then
	pythoncmd="/usr/bin/python2.6"
else
	# here's hoping!
	pythoncmd="/usr/bin/python"
fi

pythonfile="/usr/share/conkygooglecalendar/conkyGoogleCalendar.py"

exec $pythoncmd $pythonfile "$@"

```

I've updated the local files so in the next release this fix will be there, whenever it might be...

---

### Post by ayryq on 2011-02-11
> **KenJean said:**
> I hope this isn't just me:

Something appears to be broken with the -f switch.

Heretofore -f "%a %m-%d" produced the output "Tue 11-30". Now it only produces "Tue"

It appears that the space in the format string is causing the truncation, because -f "%a%m-%d" will produce "Tue11-30"

Any ideas?

-KJ

Me too. Have you solved this problem?

---

### Post by kaivalagi on 2011-02-12
> **ayryq said:**
> Me too. Have you solved this problem?

Yep, just not released the updated package yet, I was waiting for more changes first...if you sudo edit /usr/bin/conkyGoogleCalendar with the below it should solve the problem:

```
#! /bin/sh
cd /usr/share/conkygooglecalendar/

if [ -f /usr/bin/python2 ]; then
	pythoncmd="/usr/bin/python2"
elif [ -f /usr/bin/python2.7 ] ; then
	pythoncmd="/usr/bin/python2.7"
elif [ -f /usr/bin/python2.6 ] ; then
	pythoncmd="/usr/bin/python2.6"
else
	# here's hoping!
	pythoncmd="/usr/bin/python"
fi

pythonfile="/usr/share/conkygooglecalendar/conkyGoogleCalendar.py"

exec $pythoncmd $pythonfile "$@"

```

If you'd had read the last post before yours you would have seen the solution.......

---

### Post by kaivalagi on 2011-02-12
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to handle spaces in arguments so long as they are used in quotes themselves
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.11_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.11_source.changes)

The apt packages should be available soon

---

### Post by ayryq on 2011-02-12
> **kaivalagi said:**
> 
If you'd had read the last post before yours you would have seen the solution.......

Sorry, and thank you. I saw the above but didn't realize it would apply to both the spaces-in-calendar-names problem (which I had worked around by changing calendar names) and the spaces-in-date-formats problem. Updated via apt and it's working great.

My only remaining problem is it choking when I use an en-dash (—) in my template.

Thanks again for your great scripts.
eric

---

### Post by kaivalagi on 2011-02-12
> **ayryq said:**
> Sorry, and thank you. I saw the above but didn't realize it would apply to both the spaces-in-calendar-names problem (which I had worked around by changing calendar names) and the spaces-in-date-formats problem. Updated via apt and it's working great.

My only remaining problem is it choking when I use an en-dash (—) in my template.

Thanks again for your great scripts.
eric

No worries and re-reading that post I can see how you might not realise it would remedy your issue.

Not got the Linux box right now, kids have taken over to watch a movie so I can't see what he error would be for that character in the template. I assume it has something to do with ascii / unicode?

---

### Post by ayryq on 2011-02-12
Couldn't tell you. There is no error at the console, the output is as expected (with the dash) except for the ${} tags aren't parsed.

In Conky, though, there is NO output from the template at all when the dash is present.

Eric

---

### Post by kaivalagi on 2011-02-12
> **ayryq said:**
> Couldn't tell you. There is no error at the console, the output is as expected (with the dash) except for the ${} tags aren't parsed.

In Conky, though, there is NO output from the template at all when the dash is present.

Eric

Looks like you've found an quirky issue with conky then...

---

### Post by ayryq on 2011-02-12
> **kaivalagi said:**
> Looks like you've found an quirky issue with conky then...

I think I must be running into a problem with execpi. I'm getting other weird things too:

My template:  [title]${goto 180}[starttime]${alignr}[endtime]

And I get output like this (only in conky; works at console when calling conkyGoogleCalendar directly):
```

event2     Wed (02/16) 10:30      Wed (02/16) 11:30
event3     Thu (02/17) 19:00      Thu (02/17) 21:30
event4     Fri (02/18)${align}r   

```

---

### Post by kaivalagi on 2011-02-12
> **ayryq said:**
> I think I must be running into a problem with execpi. I'm getting other weird things too:

My template:  [title]${goto 180}[starttime]${alignr}[endtime]

And I get output like this (only in conky; works at console when calling conkyGoogleCalendar directly):
```

event2     Wed (02/16) 10:30      Wed (02/16) 11:30
event3     Thu (02/17) 19:00      Thu (02/17) 21:30
event4     Fri (02/18)${align}r   

```

There are a lot of issues/bugs with conky 1.8.1 and align/goto's not working when used through execp/execpi...if you can install 1.8.0 it might be worth a go...

---

### Post by tegryan on 2011-02-15
I have been using this script for months and it's worked flawlessly.  However, just recently, it's stopped working.  The command line error I get is:

```
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 119, in __init__
    self.getCalendarList()
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 142, in getCalendarList
    calendars.entry.sort(lambda x, y:
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 143, in <lambda>
    cmp(order[x.access_level.value],
KeyError: 'root'

No Events...
```

I've searched for an answer through this forum but couldn't find any.

Any help would be greatly appreciated.

Thanks!

---

### Post by TJLeJeune on 2011-02-22
hey kaivalagi, love your work. Im currently using the conkyBanshee, conkyForecast, conkyGoogleCalendar, and conkyTransmission scripts for a while now and all work great.  Anyways im not sure if you've seen this yet but it looks pretty interesting. 

[http://code.google.com/p/pygooglevoice/](http://code.google.com/p/pygooglevoice/)

google voice sms and voice mail transcripts would be awesome in conky. Anyways thank for making my conky that much more useful

---

### Post by kaivalagi on 2011-02-23
When they bring google voice to the UK I'll take a look, right now it just sin't available and I am not going to let all you google voice users have all the fun whilst I can't! :P

---

### Post by kaivalagi on 2011-02-26
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added keyring functionality so no clear text passwords need to be used, use the conkyKeyring tool to set passwords 
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.12_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.12_source.changes)

The apt packages should be available soon


[SIZE="3"]**Hints and Tips**[/SIZE]

Here's the help from conkyKeyring:
```
Usage: conkyKeyring [options]

Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        The username where the password will be stored
                        against, this is usually an email address or other
                        account identifier which is used for login purposes
  -p PASSWORD, --password=PASSWORD
                        The password to be stored safely, leave unset to
                        retrieve the password
  -d, --delete          If set the password associated with the username given
                        is deleted
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

As an example I setup my gmail account first off by assigning a password to it like so:

```
conkyKeyring -u USER@gmail.com -p PASSWORD
```

I then use the gcal script to get the calendar details as follows:

```
conkyGoogleCalendar -u USER@gmail.com
```

If no -p/--password argument is given the password is expected to be in the keyring and an attempt to retrieve it is made...

Thanks to donoterase for getting the ball rolling with the email script, I hope my choice of approach works for everyone

Chimo

---

### Post by kaivalagi on 2011-03-18
**[COLOR=RoyalBlue][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added [completetime] and [duration] to the template options, changed the default template and updated date time format handling
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.14_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.14_source.changes)

The apt packages should be available soon

---

### Post by derklempner on 2011-03-18
> **kaivalagi said:**
> **[COLOR=RoyalBlue][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added [completetime] and [duration] to the template options, changed the default template and updated date time format handling
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.14_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.14_source.changes)

The apt packages should be available soon
There seems to be an issue with your most recent update...
```
xxxxx@charon:~$ conkyGoogleCalendar -u derklempner -r xxxxx -d 8 -l 5 -n -t /home/xxxxx/.conky_goocal
Please input your password for the keyring
Password: 
ERROR: getFutureEvents:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 353, in getFutureEvents
    if self.getDateFromWhen(when.end_time) > now:
AttributeError: GoogleCalendarInfo instance has no attribute 'getDateFromWhen'

No Events...
```
That's the output I get every time I try to run the script.

---

### Post by kaivalagi on 2011-03-18
> **derklempner said:**
> There seems to be an issue with your most recent update...
```
xxxxx@charon:~$ conkyGoogleCalendar -u derklempner -r xxxxx -d 8 -l 5 -n -t /home/xxxxx/.conky_goocal
Please input your password for the keyring
Password: 
ERROR: getFutureEvents:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 353, in getFutureEvents
    if self.getDateFromWhen(when.end_time) > now:
AttributeError: GoogleCalendarInfo instance has no attribute 'getDateFromWhen'

No Events...
```
That's the output I get every time I try to run the script.

Thanks, I can reproduce it too, I'm on it

edit: can you replace /usr/share/conkygooglecalendar/conkyGoogleCalendar.py with the zipped version attached please? Then hopefully confirm it works? Once I know I'll rollout an update.....cheers

---

### Post by derklempner on 2011-03-18
> **kaivalagi said:**
> Thanks, I can reproduce it too, I'm on it

edit: can you replace /usr/share/conkygooglecalendar/conkyGoogleCalendar.py with the zipped version attached please? Then hopefully confirm it works? Once I know I'll rollout an update.....cheers
Working fine now.  Looks good!  And thanks for the most excellent script from which I get a lot of use!

---

### Post by kaivalagi on 2011-03-18
> **derklempner said:**
> Working fine now.  Looks good!  And thanks for the most excellent script from which I get a lot of use!

No probs, I was a little slack with this change...hope you like the formatting additions though...let me know if anything else is off at all!

Expect a new package with the fix included soon

Cheers

---

### Post by derklempner on 2011-03-18
I do have one question, though...
I can't seem to figure out how to get the script to work with my keyring.  No matter what I do, it asks for the keyring password.

---

### Post by kaivalagi on 2011-03-18
> **derklempner said:**
> I do have one question, though...
I can't seem to figure out how to get the script to work with my keyring.  No matter what I do, it asks for the keyring password.

Mmmmm, so you've set the password up for the user with conkyKeyring and then it doesn't like using it?

---

### Post by derklempner on 2011-03-18
> **kaivalagi said:**
> Mmmmm, so you've set the password up for the user with conkyKeyring and then it doesn't like using it?
Exactly.  Here's what happens every time I run it:
```
xxxxx@charon:~$ conkyGoogleCalendar -u derklempner -r xxxxx -d 8 -l 5 -n -t /home/xxxxx/.conky_goocal
Please input your password for the keyring
Password:
```

---

### Post by kaivalagi on 2011-03-18
> **derklempner said:**
> Exactly.  Here's what happens every time I run it:
```
xxxxx@charon:~$ conkyGoogleCalendar -u derklempner -r xxxxx -d 8 -l 5 -n -t /home/xxxxx/.conky_goocal
Please input your password for the keyring
Password:
```


Just to explain, to setup a password:

```
conkyKeyring -u USER -p PASSWORD
```

if you then call the script as follows it should display the password:

```
conkyKeyring -u USER
```

Maybe it's worth deleting the username/password first using "conkyKeyring -U USER -d" first then going through the above steps?

If you've done all that and it still asks for a password to access the keyring data then I know as much as you....I'd hazard a guess it is distro specific as I don't have this issue....any googling on this would best be done using the keywords "python keyring". This is the module I used: [http://pypi.python.org/pypi/keyring](http://pypi.python.org/pypi/keyring)

---

### Post by derklempner on 2011-03-18
> **kaivalagi said:**
> Just to explain, to setup a password:

```
conkyKeyring -u USER -p PASSWORD
```

if you then call the script as follows it should display the password:

```
conkyKeyring -u USER
```

Maybe it's worth deleting the username/password first using "conkyKeyring -U USER -d" first then going through the above steps?

If you've done all that and it still asks for a password to access the keyring data then I know as much as you....I'd hazard a guess it is distro specific as I don't have this issue....any googling on this would best be done using the keywords "python keyring". This is the module I used: [http://pypi.python.org/pypi/keyring](http://pypi.python.org/pypi/keyring)
Yeah, I followed all the steps to create the password for the user, but what I didn't have was the Python backend for GNOME Keyring (Seahorse)!  I installed that, then deleted the user and recreated it with the correct password.  Finally, I tested it and it worked perfectly.

Thanks again!

---

### Post by kaivalagi on 2011-03-18
> **derklempner said:**
> Yeah, I followed all the steps to create the password for the user, but what I didn't have was the Python backend for GNOME Keyring (Seahorse)!  I installed that, then deleted the user and recreated it with the correct password.  Finally, I tested it and it worked perfectly.

Thanks again!

mmmmm, you mean "python-keyring" was missing? What package name did you need to install? Not "seahorse" itself? I can make sure it's a dependency if it isn't already

---

### Post by kaivalagi on 2011-03-18
**[COLOR=Orange][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]bug fix: issue found with future events functionality, function name changes weren't rolled out to all code paths...oops
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.15_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.15_source.changes)

The apt packages should be available soon

---

### Post by derklempner on 2011-03-24
> **kaivalagi said:**
> mmmmm, you mean "python-keyring" was missing? What package name did you need to install? Not "seahorse" itself? I can make sure it's a dependency if it isn't already
Yes, **python-keyring** wasn't installed.  Perhaps you should make it a dependancy.

---

### Post by kaivalagi on 2011-03-24
> **derklempner said:**
> Yes, **python-keyring** wasn't installed.  Perhaps you should make it a dependancy.

Mmmmm, it should be....I'll double check now
edit: it already is a dependency :confused:

---

### Post by neodebian on 2011-04-07
Great job I have tested many of your scripts and it works great. I have just a quick question and I don't find the answer for the moment.

Is it possible to include TIMEFORMAT in the template like this for example?

```
${color #3399FF}Debut: ${color1}[starttime] ${color #3399FF}Fin: ${color1}[endtime --dateformat="" --timeformat="%H:%M"]

```

---

### Post by Sector11 on 2011-04-07
> **neodebian said:**
> Great job I have tested many of your scripts and it works great. I have just a quick question and I don't find the answer for the moment.

Is it possible to include TIMEFORMAT in the template like this for example?

```
${color #3399FF}Debut: ${color1}[starttime] ${color #3399FF}Fin: ${color1}[endtime --dateformat="" --timeformat="%H:%M"]

```

Yes, it should work, did you try it?

```
Usage: conkyGoogleCalendar [options]
Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        Username for login into Google Calendar, this will
                        normally be your gmail account
  -p PASSWORD, --password=PASSWORD
                        Password for login
  -r TEXT, --requestCalendarNames=TEXT
                        Define a list of calendars to request event data for,
                        calendar names should be separated by semi-colons ";".
                        For example --requestCalendarNames="cal1;cal2;other
                        cal" If not set all calendar data will be returned.
  -d NUMBER, --daysahead=NUMBER
                        [default: 7] Define the number of days ahead you wish
                        to retrieve calendar entries for, starting from today.
  -s DATE, --startdate=DATE
                        Define the start date to retrieve calendar events. In
                        the form '2007-12-01'
  -e DATE, --enddate=DATE
                        Define the end date to retrieve calendar events, must
                        be supplied if --startdate supplied. In the form
                        '2007-12-01'
  -a, --allevents       Retrieve all calendar events
  -w TEXT, --wordsearch=TEXT
                        Define the text to search calendar entries with.
  -l NUMBER, --limit=NUMBER
                        [default: 0] Define the maximum number of calendar
                        events to display, zero means no limit.
  -t FILE, --template=FILE
                        Template file determining the format for each event.
                        Use the following placeholders: [title], [starttime],
                        [endtime], [location], [description], [who]. Ensure
                        only one placeholder per line, as the whole line is
                        removed if no data for that placeholder exists.
  -f "DATEFORMAT", --dateformat="DATEFORMAT"
                        If used this overrides the default date formatting.
                        The values to use are standard formatting strings e.g.
                        Weekday=%a, Day=%d, Month=%m, Year=%y. For an output
                        like "Thu 15/10/2008" you would require
                        --dateformat="%a %d/%m/%y", to have no date you would
                        require --dateformat=""
  -F "TIMEFORMAT", **[COLOR="Blue"]--timeformat="TIMEFORMAT"[/COLOR]**
                        If used this overrides the default time formatting.
                        The values to use are standard formatting strings e.g.
                        Hours (12hr)=%l, Hours (24hr)=%H, Minutes=%M,
                        Seconds=%S, AM/PM=%P. For an output like "05:22 PM"
                        you would require --timeformat="%l:%M %P",
                        --timeformat="" is not supported, default locale
                        settings are used
  -i NUMBER, --indent=NUMBER
                        [default: 0] Define the number of spaces to indent the
                        output (excludes template based output)
  -m NUMBER, --maxwidth=NUMBER
                        [default: 40] Define the number of characters to
                        output per line
  -n, --nowho           Hides who is attending the events (excludes template
                        based output)
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

---

### Post by neodebian on 2011-04-08
> **Sector11 said:**
> Yes, it should work, did you try it?

```
Usage: conkyGoogleCalendar [options]
Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        Username for login into Google Calendar, this will
                        normally be your gmail account
  -p PASSWORD, --password=PASSWORD
                        Password for login
  -r TEXT, --requestCalendarNames=TEXT
                        Define a list of calendars to request event data for,
                        calendar names should be separated by semi-colons ";".
                        For example --requestCalendarNames="cal1;cal2;other
                        cal" If not set all calendar data will be returned.
  -d NUMBER, --daysahead=NUMBER
                        [default: 7] Define the number of days ahead you wish
                        to retrieve calendar entries for, starting from today.
  -s DATE, --startdate=DATE
                        Define the start date to retrieve calendar events. In
                        the form '2007-12-01'
  -e DATE, --enddate=DATE
                        Define the end date to retrieve calendar events, must
                        be supplied if --startdate supplied. In the form
                        '2007-12-01'
  -a, --allevents       Retrieve all calendar events
  -w TEXT, --wordsearch=TEXT
                        Define the text to search calendar entries with.
  -l NUMBER, --limit=NUMBER
                        [default: 0] Define the maximum number of calendar
                        events to display, zero means no limit.
  -t FILE, --template=FILE
                        Template file determining the format for each event.
                        Use the following placeholders: [title], [starttime],
                        [endtime], [location], [description], [who]. Ensure
                        only one placeholder per line, as the whole line is
                        removed if no data for that placeholder exists.
  -f "DATEFORMAT", --dateformat="DATEFORMAT"
                        If used this overrides the default date formatting.
                        The values to use are standard formatting strings e.g.
                        Weekday=%a, Day=%d, Month=%m, Year=%y. For an output
                        like "Thu 15/10/2008" you would require
                        --dateformat="%a %d/%m/%y", to have no date you would
                        require --dateformat=""
  -F "TIMEFORMAT", **[COLOR="Blue"]--timeformat="TIMEFORMAT"[/COLOR]**
                        If used this overrides the default time formatting.
                        The values to use are standard formatting strings e.g.
                        Hours (12hr)=%l, Hours (24hr)=%H, Minutes=%M,
                        Seconds=%S, AM/PM=%P. For an output like "05:22 PM"
                        you would require --timeformat="%l:%M %P",
                        --timeformat="" is not supported, default locale
                        settings are used
  -i NUMBER, --indent=NUMBER
                        [default: 0] Define the number of spaces to indent the
                        output (excludes template based output)
  -m NUMBER, --maxwidth=NUMBER
                        [default: 40] Define the number of characters to
                        output per line
  -n, --nowho           Hides who is attending the events (excludes template
                        based output)
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

Yes It works on the command line but I don't find the way to format one output in the template. For the beginning i Want the day and Hour but I try to just put the Hour in short format for the end.

---

### Post by kaivalagi on 2011-04-08
> **neodebian said:**
> Great job I have tested many of your scripts and it works great. I have just a quick question and I don't find the answer for the moment.

Is it possible to include TIMEFORMAT in the template like this for example?

```
${color #3399FF}Debut: ${color1}[starttime] ${color #3399FF}Fin: ${color1}[endtime --dateformat="" --timeformat="%H:%M"]

```

Nope timeformat is not for templates, as the this scripts template is for a single event not overall operation (the list of items for a template are listed in the -t/--template help text). Just use the timeformat option in the main exec call where you also point to a template...simples

e.g. conkyrc:
```
{execpi 600 conkyGoogleCalendar ...options... --dateformat="" --timeformat="%H:%M" --template=path/to/template}
```

also note that the latest version of the script has additional formatted outputs for template use:

```
  -t FILE, --template=FILE
                        Template file determining the format for each event.
                        Use the following placeholders: [title], [starttime],
                        [endtime], **[completetime], [duration]**, [location],
                        [description], [who]. Ensure only one placeholder per
                        line, as the whole line is removed if no data for that
                        placeholder exists.
```

I think completetime might do what you want....it will exclude the date portion is not needed between two datetimes etc

---

### Post by neodebian on 2011-04-08
Prefect as usual it's exactly what I need. Many thanks for your help.:D

---

### Post by Sector11 on 2011-04-08
In my eagerness to help ... I totally over looked:

```
--timeformat="" is not supported, default locale settings are used
```

bir saying that I'm glad it worked out.

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by kaivalagi on 2011-04-24
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed conkykeyring dependency issue with some debian systems (case sensitivity)
[*]Moved 'No Events...' output from normal to logged output so it's not seen anymore in conky
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.16_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglecalendar_2.16_source.changes)

The apt packages should be available soon

---

### Post by fesghelbahal on 2011-05-05
Huh, I figured out how to work with this, I guess :)
Thanks for the great job.

---

### Post by kaivalagi on 2011-05-05
> **fesghelbahal said:**
> Huh, I figured out how to work with this, I guess :)
Good for you, once you get the knack of the options you'll find it can do quite a bit...

> **fesghelbahal said:**
> Thanks for the great job.
Cheers

---

### Post by wolfbiteaus on 2011-06-21
Hi, have everything working nicely 

but getting a bit of a quirk in the output

I have events where I keep track of bill days

so might have some events 

birthday 1973
loan $200
dinner $87.56

when I display the event it comes out  
birthday 173
loan ${200}
dinner ${87}.56

this was tested with your example script & template also
same results

seems to be reading the advent and acting on the $ symbol
I could leave out the $ as a work around
but the event should be getting display as a string and not being interpreted

any ideas??

good program anyway :)

---

### Post by kaivalagi on 2011-06-21
> **wolfbiteaus said:**
> Hi, have everything working nicely 

but getting a bit of a quirk in the output

I have events where I keep track of bill days

so might have some events 

birthday 1973
loan $200
dinner $87.56

when I display the event it comes out  
birthday 173
loan ${200}
dinner ${87}.56

this was tested with your example script & template also
same results

seems to be reading the advent and acting on the $ symbol
I could leave out the $ as a work around
but the event should be getting display as a string and not being interpreted

any ideas??

good program anyway :)

Unfortunately the $ symbol is key to conky variables, as such anything being returned via the script from a template with a preceding $ through the execp/execpi method will get parsed and treated as a conky variable if at all like one. But there might be a way around that...

You can escape one $ with a second, so in a template '$$100' will come out rendered as '$100'....testing with some command line calls confirms the escaping:

[INDENT]```
conky -a middle_middle -t 'birthday 1973\nloan $$200\ndinner $$87.56'
```
produces:
```
birthday 1973
loan $200
dinner $87.56
```
[/INDENT]

Maybe I need to have a replace function for calendar data to change $ to $$ so conky ignores it.....I may be back with a replacement script for you to test with ;)

[COLOR="Navy"]edit: give the attached a try and let me know the outcome, I've not tested it at all but it should work in theory!

Just extract it over the top of /usr/share/conkygooglecalendar/conkyGoogleCalendar.py (you may want to backup the original file first)[/COLOR]

---

### Post by aleblanc on 2011-06-22
Hi, I love your script but I made an alteration so that if the date on an event is today or tomorrow it prints "Today!!" or "Tomorrow" instead of the actual date (so I'm more likely to take notice).

Also, I couldn't get it to work with google tasks, but found a bash script [here]("https://bbs.archlinux.org/viewtopic.php?id=112308") to do the job. I modified it slightly to work with conky's "execi" command.
So you just use for example; ${execi 600 /path/to/googleTasks.sh}
in your .conkyrc (after replacing <USERNAME> and <PASSWORD> with your username and password)

I have attached both files.

---

### Post by kaivalagi on 2011-06-22
> **wolfbiteaus said:**
> seems to be reading the advent and acting on the $ symbol
I could leave out the $ as a work around
but the event should be getting display as a string and not being interpreted

any ideas??


> **kaivalagi said:**
> [COLOR="Navy"]edit: give the attached a try and let me know the outcome, I've not tested it at all but it should work in theory!

Just extract it over the top of /usr/share/conkygooglecalendar/conkyGoogleCalendar.py (you may want to backup the original file first)[/COLOR]

Had another look and I doubt the fix would have worked, once there please try the version of the file attached in this post...it will handle dollar signs in title, description and location fields once I've done it :)

> **aleblanc said:**
> Hi, I love your script but I made an alteration so that if the date on an event is today or tomorrow it prints "Today!!" or "Tomorrow" instead of the actual date (so I'm more likely to take notice).
When I get a chance I'll have a play and see what I think, time is scarce though

> **aleblanc said:**
> Also, I couldn't get it to work with google tasks, but found a bash script [here]("https://bbs.archlinux.org/viewtopic.php?id=112308") to do the job. I modified it slightly to work with conky's "execi" command.
So you just use for example; ${execi 600 /path/to/googleTasks.sh}
in your .conkyrc (after replacing <USERNAME> and <PASSWORD> with your username and password)
Interesting....tasks are not calendar entries so they most definitely aren't supported in this script...I might have to create a conkyGoogleTask script in python that borrows some of the functionality from the script...I'll take a look soon(ish).

Thanks!

edit: I'll do the today / tomorrow thing in the next release, lost the exclamation mark though....just don't like them....nothing's that important :)
I don't like the curl script, it can't handle anything other than the default task list, I use several...but there is enough to go on there to make a script by adapting the conkyGoogleReader script I made I think...it uses URLs, Google auth through headers etc...just need to parse the javascript returned....maybe there is a way to request the task lists by name?

edit2: The attached has both a working fix for $'s inside event data and the today/tomorrow change...cheers

---

### Post by jackofall0 on 2011-06-23
Hey all-

Just wondering if there was a way to remove duplicate entries?  That is if two events have the same title, day and time, only one should show?

---

### Post by kaivalagi on 2011-06-23
> **jackofall0 said:**
> Hey all-

Just wondering if there was a way to remove duplicate entries?  That is if two events have the same title, day and time, only one should show?

You have 2 from just one calendar or is it where you have multiple calendars?

---

### Post by jackofall0 on 2011-06-23
> **kaivalagi said:**
> You have 2 from just one calendar or is it where you have multiple calendars?

No, multiple calendars.

---

### Post by kaivalagi on 2011-06-23
> **jackofall0 said:**
> No, multiple calendars.

I can make sure the list is unique quite quickly if it is based on all info e.g. title, start time, end time, location, description and who

Would that work for you?  Or would it need to be just title, start time and end time?

I've attached an updated script to handle the first suggestion :)

---

### Post by jackofall0 on 2011-06-23
> **kaivalagi said:**
> I can make sure the list is unique quite quickly if it is based on all info e.g. title, start time, end time, location, description and who

Would that work for you?  Or would it need to be just title, start time and end time?

I've attached an updated script to handle the first suggestion :)

The attached script works, but sometimes an event has "Who:A,B" on one calendar and "Who:B,A" on the other.  These events are not unique and the order of attendees doesn't really matter.

I think the best way is just title, start, and end time.

Thanks for the fast response!

---

### Post by kaivalagi on 2011-06-23
> **jackofall0 said:**
> The attached script works, but sometimes an event has "Who:A,B" on one calendar and "Who:B,A" on the other.  These events are not unique and the order of attendees doesn't really matter.

I think the best way is just title, start, and end time.

Thanks for the fast response!

I've had a little play and I agree that the "who" gets in the way, I setup 2 equivalent events with matching everything but the who made them unique

I've done as you requested, removed duplicates based on title, starttime and endtime, but only if the --distinctevents / -D options is used

See attached, let me know if that works for you :)

---

### Post by jackofall0 on 2011-06-23
> **kaivalagi said:**
> I've had a little play and I agree that the "who" gets in the way, I setup 2 equivalent events with matching everything but the who made them unique

I've done as you requested, removed duplicates based on title, starttime and endtime, but only if the --distinctevents / -D options is used

See attached, let me know if that works for you :)

Perfect.  Many thanks!

---

### Post by kaivalagi on 2011-06-23
> **jackofall0 said:**
> Perfect.  Many thanks!

No worries, it will be in the next release of the script....


**@ALL**
So far the next version has got:

[LIST]
[*] Updated to replace any $ symbol with $$ for event data so conky doesn't parse text as variables
[*] Update to display Today and Tomorrow on those days rather than the date
[*] Added --distinctevents / -D option which removes duplicate events with matching title, starttime and endtime
[/LIST]

Any more ideas?

---

### Post by geazzy on 2011-06-24
great threads :)

---

### Post by kaivalagi on 2011-06-24
> **geazzy said:**
> great threads :)

Glad you like ;)

---

### Post by scotteik36 on 2011-07-01
i am very new to this conky script stuff and to linux in general. i am unable to get the calendar to display anything in conky. i honestly have no idea how to fix this. let me know what i need to post in order to get help.

---

### Post by kaivalagi on 2011-07-02
Have you looked at the example files in /usr/share/conkygooglecalendar/example

If you copy those somewhere else and edit them to have your login credentials that will get you started...run this once they're edited to get something on the script:

```
conky -c /your/new/path/to/conkyrc

```

Hope that helps

---

### Post by vancheese on 2011-07-19
Hi Hi

This script rocks - Thanks :)

My only problem is that I share a calendar which use accents (like é, Ó ) and hence I get the unicode error

```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)
```

Is there a way to replace these characters with a "naked" vowel?

---

### Post by Sector11 on 2011-07-19
> **vancheese said:**
> Hi Hi

This script rocks - Thanks :)

My only problem is that I share a calendar which use accents (like é, Ó ) and hence I get the unicode error

```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)
```

Is there a way to replace these characters with a "naked" vowel?

Conky can display those.  Do you have
```
override_utf8_locale yes
```
above TEXT?

```
xftfont DejaVu Sans Mono:size=15
override_utf8_locale yes
TEXT
My only problem is that I share a calendar
which use accents (like é, Ó ) and hence I
get the unicode error

Conky is capable of displaying those and
more:

 ñ  ü  ò  ¿  ¡ ù
```

---

### Post by vancheese on 2011-07-19
Yes, my .conkyrc is just like that and it can produce the appropriate characters in the TEXT section - the corresponding error is ...

```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
    File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 579, in getOutputFromTemplate
                        output = output.replace("[duration]",duration)
                                                                      UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)
```

---

### Post by dunnemann on 2011-08-13
Kaivalagi your script works very nice, but some times I'm offline and this don't work in this mode, is there any way to pass the output of the script to a text file with the same format like on the terminal and by this way always have the google calendar on the screen.

I wish this because I use GC like to-do list.


*****I did it, I could go out of google calendar to a file using cat and sed with a shell script, thanks anyway.

---

### Post by xablins on 2011-08-18
> **vancheese said:**
> Yes, my .conkyrc is just like that and it can produce the appropriate characters in the TEXT section - the corresponding error is ...

```
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
    File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 579, in getOutputFromTemplate
                        output = output.replace("[duration]",duration)
                                                                      UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)
```

I have the same error.

Im from Brazil and every week in saturday (in brazilian write sábado) i recive that error and i put override_utf8_locale yes
ando i use this code:



TEXT

${iconv_start UTF-8 ISO_8859-1}
${execpi 1800 conkyGoogleCalendar --username=email --password=password --daysahead=30 --dateformat="%A %d %b, %y"
${iconv_stop}

Thanks for help

---

### Post by Walkerpt on 2011-11-09
ERROR: getOutputFromTemplate:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkygooglecalendar/conkyGoogleCalendar.py", line 579, in getOutputFromTemplate
    output = output.replace("[duration]",duration)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 17: ordinal not in range(128)


Este erro acontece se existirem eventos no sabado (em Portugal e Brasil Sáb).
A solução com o iconv mantém o erro.
Se não existirem eventos no sábado não apresenta qualquer erro.

Português>Inglês

This error happens if there are events on Saturday (in Portugal and Brazil Sáb).
With iconv keeps the error.
If there are no events on Saturday shows no error.

Any Help?

---

### Post by shuipi21 on 2011-11-10
Although it is something a few years ago, but still very help stick.

---

### Post by Walkerpt on 2011-11-10
Um esclarecimento.
Li todo este forum tentei as varias soluções mas nenhuma resolveu o problema.
No entanto para que se saiba o script roda no meu Uuntu 11.10 (unity).
E ao Sábado é sempre feriado :tongue:.

Português > Inglês

A clarification.
I read all this forum tried the various solutions but none solved the problem.
However, for knowing the script runs on my Uuntu 11.10 (unity).
And Saturday is always holiday :tongue:.

---

### Post by Sector11 on 2011-11-10
> **Walkerpt said:**
> Um esclarecimento.
Li todo este forum tentei as varias soluções mas nenhuma resolveu o problema.
No entanto para que se saiba o script roda no meu Uuntu 11.10 (unity).
E ao Sábado é sempre feriado :tongue:.

Português > Inglês

A clarification.
I read all this forum tried the various solutions but none solved the problem.
However, for knowing the script runs on my Uuntu 11.10 (unity).
And Saturday is always holiday :tongue:.

```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 17: ordinal not in range
```

O **á** em **Sáb** talvez?

---

### Post by Walkerpt on 2011-11-10
> **Sector11 said:**
> ```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 17: ordinal not in range
```

O **á** em **Sáb** talvez?

Sector11 Português, Brasileiro, :confused: 

Sobre o problema, também penso que é esse o problema, tal como o xablins (post 457) e antes também o vancheese (post 453) com os ó, neste último caso a sugestão dada até por Sector11 :-k aqui não resolve pois já está considerada, e a outra também refiro no meu post inicial, por isso aqui o problema mantêm-se e sem que eu perceba como o resolver.

Português>English

About the problem, I also think that this is the problem, such as xablins (post 457) and also before vancheese (post 453) with O in the latter case the suggestion given by Sector11 :-k here does not solve it already considered, and the other also mean in my initial post, so here the question remains open and without my knowing how to solve it.

---

### Post by Sector11 on 2011-11-10
> **Walkerpt said:**
> Sector11 Português, Brasileiro, :confused: 

Canadian

> **Walkerpt said:**
> Sobre o problema, também penso que é esse o problema, tal como o xablins (post 457) e antes também o vancheese (post 453) com os ó, neste último caso a sugestão dada até por Sector11 :-k aqui não resolve pois já está considerada, e a outra também refiro no meu post inicial, por isso aqui o problema mantêm-se e sem que eu perceba como o resolver.

Português>English

About the problem, I also think that this is the problem, such as xablins (post 457) and also before vancheese (post 453) with O in the latter case the suggestion given by Sector11 :-k here does not solve it already considered, and the other also mean in my initial post, so here the question remains open and without my knowing how to solve it.

Sorry - I did not see the other posts.  I have no answer - yet - I will continue to look.

Lamentable - no vi los otros "posts". No tengo ninguna respuesta - aún - seguiré mirando.

---

### Post by kgadek on 2012-01-11
Hiding certain events can be misleading. Actually, I'd better like if the script would lose some single, problematic letters... And so I made this horrible, little fix.

How to use? Save the following as horribleFix.patch and check whether this fix apply:
$ patch --dry-run -p1 -i horribleFix.patch /usr/share/conkygooglecalendar/conkyGoogleCalendar.py
If this prints "patching file /usr/share/conkygooglecalendar/conkyGoogleCalendar.py" or similar, then everything is OK. Do real fixing by calling as root:
# patch -p1 -i horribleFix.patch /usr/share/conkygooglecalendar/conkyGoogleCalendar.py

As some say -- this works for me.

```
*** /usr/share/conkygooglecalendar/conkyGoogleCalendar.py	2012-01-12 02:10:42.000000000 +0100
--- .conky/myConkyGCalMod.py	2012-01-12 02:29:10.038323060 +0100
***************
*** 432,438 ****
              starttime = self.getDatetimeString(starttime)
              endtime = self.getDatetimeString(endtime)
          
!         return starttime, endtime, completetime, duration
  
      def getDatetimeString(self,whendatetime, format=None):
  
--- 432,440 ----
              starttime = self.getDatetimeString(starttime)
              endtime = self.getDatetimeString(endtime)
          
!         def safeUnicode(x):
!             return unicode(x is not None and str(x) or "", errors='ignore')
!         return safeUnicode(starttime), safeUnicode(endtime), safeUnicode(completetime), safeUnicode(duration)
  
      def getDatetimeString(self,whendatetime, format=None):
  
***************
*** 677,683 ****
                                  #who = self.getWrappedText(who, self.options.maxwidth, indent)
  
                      # output event data using the template
!                     output = self.getOutputFromTemplate(template, title, starttime, endtime, location, description, who)
  
                      output = self.getMadeSafeOutput(output)
                      print output #.encode("utf-8")
--- 678,686 ----
                                  #who = self.getWrappedText(who, self.options.maxwidth, indent)
  
                      # output event data using the template
!                     def safeUnicode(x):
!                         return unicode(x is not None and x or "", errors='ignore')
!                     output = self.getOutputFromTemplate(template, safeUnicode(title), starttime, endtime, location, safeUnicode(description), who)
  
                      output = self.getMadeSafeOutput(output)
                      print output #.encode("utf-8")
```

---

### Post by GrouchyGaijin on 2013-01-12
I have a question for anyone using Ubuntu 12.04.
Are you able to change colors in the conky templates that are used in a number of K's scripts?

```
 ${color2}
```

or

 ```
${color yellow}
```

commands only give me text in the conky that is identical to the code I enter in the template. That is, I see ${color2} on the screen.

---

### Post by primolarry on 2013-02-17
Hi there,

I added a few lines to the getOutputFromTemplate method to avoid the utf8 problem. I didn't want to spend a lot of time in it, so the code is not perfect, but it solved the problem:

> def getOutputFromTemplate(self, template, title, starttime, endtime, location, description, who):

        try:

            output = template

            if title == None or title.strip() == "":
                output = self.removeLineByString(output,"[title]")
            else:
                **title = title.decode('utf8')**
                output = output.replace("[title]",title)

            if location == None or location.strip() == "":
                output = self.removeLineByString(output,"[location]")
            else:
                **location = location.decode('utf8')**
                output = output.replace("[location]",location)

            if description == None or description.strip() == "":
                output = self.removeLineByString(output,"[description]")
            else:
                **description = description.decode('utf8')**
                output = output.replace("[description]",description)

            if who == None or who.strip() == "":
                output = self.removeLineByString(output,"[who]")
            else:
                #output = output.replace("[who]",";".join(who))
               ** who = who.decode('utf8')**
                output = output.replace("[who]",who)

            starttime, endtime, completetime, duration = self.getFormattedEventTimes(starttime, endtime)

            **starttime = starttime.decode('utf8')**
            output = output.replace("[starttime]",starttime)
           ** endtime = endtime.decode('utf8')**
            output = output.replace("[endtime]",endtime)

            if output.find("[completetime]") != -1:
              **  completetime = completetime.decode('utf8')**
                output = output.replace("[completetime]",completetime)

            if output.find("[duration]") != -1:
                **duration = duration.decode('utf8')**
                output = output.replace("[duration]",duration)

            # get rid of any excess crlf's and add just one
            #output = output.rstrip(" \n")
            #output = output + "\n"

            return output

        except Exception,e:
            self.logError("getOutputFromTemplate:Unexpected error:" + traceback.format_exc())
            return ""


Regards

---

### Post by racinecubix on 2013-02-21
Thanks primolarry, this fixed the utf8 problem for me but I needed to make an additional modification on the line (#691 after your modifications):

print output #.encode("utf-8")

Simply remove the comment to get:

print output.encode("utf-8")

---

