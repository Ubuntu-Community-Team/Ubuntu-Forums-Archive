---
title: "FBuntu: Facebook Notifier for Messaging Menu"
date: 2011-03-20
forum: The Cafe
---

### Post by fluteflute on 2011-03-20
Download the code from launchpad; follow the instructions in the README to set up authentication; and finally run it!

All feedback gratefully received (preferably constructive).

```
bzr branch lp:fbuntu
cd fbuntu
mv auth.py.example auth.py
[follow the instructions in the README file to set things up]
python fbuntu.py
[wait. and look in debug.log if thing's aren't going as expected]

```
[IMG]http://i.stack.imgur.com/vLVWl.png[/IMG]

---

### Post by earthpigg on 2011-03-20
download link to the python script? :P

---

### Post by markp1989 on 2011-03-20
just tried it, having problems with the "url=" field in the auth.py file

I followed the instructions in README , and ended up on a page with a long url with "success" written on it, I copied that url in to the auth.py file and i got an error


> AttributeError: facebookAuthentication instance has no attribute 'user_id'


im sure im probably miss reading the README file.

---

### Post by fluteflute on 2011-03-21
> **markp1989 said:**
> just tried it, having problems with the "url=" field in the auth.py file

I followed the instructions in README , and ended up on a page with a long url with "success" written on it, I copied that url in to the auth.py file and i got an error


im sure im probably miss reading the README file.

The long url with "success" is exactly what we need. Sorry that was my mistake, I've updated the code. Please let me know if it still doesn't work.

> **earthpigg said:**
> download link to the python script? :P

You [can download the files individually]("http://bazaar.launchpad.net/~fluteflute/fbuntu/trunk/files") if you wish.

---

### Post by rolandixor on 2011-03-21
Gimmie a ppa, and I'll be testing.

---

### Post by fluteflute on 2011-03-21
> **rolandixor said:**
> Gimmie a ppa, and I'll be testing.

Another month or so (don't hold me to it!) and perhaps I'll have something stable and usable to the average user. At that point I'll have a look at PPA packaging.

---

### Post by markp1989 on 2011-03-21
> **fluteflute said:**
> The long url with "success" is exactly what we need. Sorry that was my mistake, I've updated the code. Please let me know if it still doesn't work.



You [can download the files individually]("http://bazaar.launchpad.net/~fluteflute/fbuntu/trunk/files") if you wish.

thanks, just downloaded the new version, it appears to be working (no errors so far) right now its just in a "Checking Facebook..." loop but I haven't received any notifications so far, but will report back when I can get a friend to "like" a post.

---

### Post by markp1989 on 2011-03-21
> **fluteflute said:**
> The long url with "success" is exactly what we need. Sorry that was my mistake, I've updated the code. Please let me know if it still doesn't work.



You [can download the files individually]("http://bazaar.launchpad.net/~fluteflute/fbuntu/trunk/files") if you wish.

thanks, just downloaded the new version, it appears to be working (no errors so far) right now its just in a "Checking Facebook..." loop but I haven't received any notifications so far, but will report back when I have.

edit: one of my friends "liked" my statuses, and I received the notification as expected :)

edit1: seems good so far, but could do with an icon as currently it looks a bit ugly in the messaging menu (screen shot attached)

---

### Post by fluteflute on 2011-03-21
> **markp1989 said:**
> edit1: seems good so far, but could do with an icon as currently it looks a bit ugly in the messaging menu (screen shot attached)

Thanks for all the feedback!

I'm actually ahead of you, so 'bzr update' and take a look at the README file once more :)

---

### Post by nilarimogard on 2011-03-21
Great but.. it downloads every single message I've ever received on Facebook and spams my Messaging Menu

---

### Post by fluteflute on 2011-03-21
> **nilarimogard said:**
> Great but.. it downloads every single message I've ever received on Facebook and spams my Messaging Menu
Inbox messages or "notifications"?

---

### Post by nilarimogard on 2011-03-21
> **fluteflute said:**
> Inbox messages or "notifications"?

Inbox messages. And I have lots of them...

---

### Post by fluteflute on 2011-03-21
> **nilarimogard said:**
> Inbox messages. And I have lots of them...
Hmmm Facebook is meant to only return threads that are marked *unread*. 

Any chance you could visit the URL below (replacing the stars with your access token from the auth.py URL) and let me know if you get lots of messages back from it (you shouldn't)?

Your help is very much appreciated.

[https://api.facebook.com/method/fql.query?format=json&query=SELECT%20snippet%2Csnippet_author%2Cupdated_time%2Cthread_id%20FROM%20thread%20WHERE%20folder_id%20%3D%200%20AND%20unread%20%21%3D%200&access_token=*****](https://api.facebook.com/method/fql.query?format=json&query=SELECT%20snippet%2Csnippet_author%2Cupdated_time%2Cthread_id%20FROM%20thread%20WHERE%20folder_id%20%3D%200%20AND%20unread%20%21%3D%200&access_token=*****)

---

### Post by nilarimogard on 2011-03-22
> **fluteflute said:**
> Hmmm Facebook is meant to only return threads that are marked *unread*. 

Any chance you could visit the URL below (replacing the stars with your access token from the auth.py URL) and let me know if you get lots of messages back from it (you shouldn't)?

Your help is very much appreciated.

[https://api.facebook.com/method/fql.query?format=json&query=SELECT%20snippet%2Csnippet_author%2Cupdated_time%2Cthread_id%20FROM%20thread%20WHERE%20folder_id%20%3D%200%20AND%20unread%20%21%3D%200&access_token=*****](https://api.facebook.com/method/fql.query?format=json&query=SELECT%20snippet%2Csnippet_author%2Cupdated_time%2Cthread_id%20FROM%20thread%20WHERE%20folder_id%20%3D%200%20AND%20unread%20%21%3D%200&access_token=*****)

Yes I did get a lot of messages. So I guess it's a Facebook issue so I'll just delete all my messages.

---

### Post by fluteflute on 2011-03-22
> **nilarimogard said:**
> Yes I did get a lot of messages. So I guess it's a Facebook issue so I'll just delete all my messages.
Okay, thanks for trying it out for me :)

---

### Post by Samineru on 2011-06-22
I'm not sure if this is still under development, but I am also receiving a list of all my messages, read or unread.

---

### Post by fluteflute on 2011-06-22
> **Samineru said:**
> I'm not sure if this is still under development, but I am also receiving a list of all my messages, read or unread.

It's kinda under development...it works for me most of the time therefore I don't have much motivation to keep developing.

Keen to figure out what's happening for you though.

Could you try out some links for me? You'll need to replace the stars with your access token from the auth.py URL

1. The method FBuntu currently uses (this will probably return all of your messages, please can you confirm that?):
```
https://api.facebook.com/method/fql.query?format=json&query=SELECT snippet,snippet_author,updated_time,thread_id FROM thread WHERE folder_id = 0 AND unread != 0&access_token=***
```

2. Can you please post the results of this one:
```
https://api.facebook.com/method/fql.query?format=json&query=SELECT unread FROM thread WHERE folder_id = 0 AND unread != 0&access_token=***
```

3. And finally, does this produce different results from #1 ?
```
https://api.facebook.com/method/fql.query?format=json&query=SELECT snippet,snippet_author,updated_time,thread_id FROM thread WHERE folder_id = 0 AND unread > 0 &access_token=***
```

Thank you!

---

### Post by fluteflute on 2011-07-04
I've just pushed a new revision that means FBuntu no longer dies when there's a blip in the internet connection (quite handy if you're on a connection like mine...)

Hopefully gonna make a few more improvements in the next few days.

---

### Post by jvgeli on 2011-07-08
this is pretty cool. Any updates on the development?

---

### Post by fluteflute on 2011-07-08
> **jvgeli said:**
> this is pretty cool. Any updates on the development?No..

Partly because it mostly does the job for me, and partly because everything is quite busy.

But is there anything you'd particularly like to see, or any problems you're having?

[One thing I'd love to fix is that clicking on an inbox message doesn't take you to the message with the new messaging system]

---

### Post by jvgeli on 2011-07-08
not really. Will use today. Would you like bugs reported?

---

### Post by fluteflute on 2011-07-08
> **jvgeli said:**
> not really. Will use today. Would you like bugs reported?Yeah please do, you can post here on report on Launchpad - whichever you preferred.

---

### Post by fluteflute on 2011-07-17
Hi everyone, I've made some fairly major updates to FBuntu!

Anyone who's interested, I'd encourage to follow the instructions in the first post. Let me know how it goes.

---

### Post by Rasa1111 on 2012-02-22
How's this going? 
Still working on it?

---

### Post by fluteflute on 2012-02-23
> **Rasa1111 said:**
> How's this going? 
Still working on it?A little. I update it to fit my needs basically... I'm well aware that it's not perfect.

Are you using it?

---

### Post by palimmo on 2012-03-08
> **fluteflute said:**
> A little. I update it to fit my needs basically... I'm well aware that it's not perfect.

Are you using it?
Hallo!
I'm trying this application.
But I can't see its icon in the menu message and my debug.log says:
```
2012-03-08 15:31:35 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
```

Moreover, I haven't seen any "success" sign after the authorization screen.

Can you help me?

--EDIT--
I did it once more with Chromium... and now it seems to work.
I'll wait to see if it shows me the notifications correctly.

---

### Post by fluteflute on 2012-03-08
> **palimmo said:**
> Hallo!
I'm trying this application.
But I can't see its icon in the menu message and my debug.log says:
```
2012-03-08 15:31:35 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
```

Moreover, I haven't seen any "success" sign after the authorization screen.

Can you help me?

--EDIT--
I did it once more with Chromium... and now it seems to work.
I'll wait to see if it shows me the notifications correctly.I'm glad it's working now. I think when an error like that occurs, I should probably provide some feedback to the user, rather than just silently exiting!

---

### Post by palimmo on 2012-03-08
It works!
(Do it with Firefox or Chromium probably is indifferent. 
I just wrongly used a false link for the authentication that I found somewhere....but the one in the README is right.)

---

### Post by palimmo on 2012-03-09
Welll. not really..
I have a private message waiting for me, but no fbuntu notification...
```

2012-03-09 10:11:32 fbuntu.py:56 INFO: Update #1 starting
2012-03-09 10:11:32 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 10:11:34 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 10:11:34 fbuntu.py:61 INFO: Ended update #1

2012-03-09 10:11:51 fbuntu.py:56 INFO: Update #2 starting
2012-03-09 10:11:51 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 10:11:52 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 10:11:52 fbuntu.py:61 INFO: Ended update #2

...

```

---

### Post by fluteflute on 2012-03-09
> **palimmo said:**
> Welll. not really..
I have a private message waiting for me, but no fbuntu notification...
```

2012-03-09 10:11:32 fbuntu.py:56 INFO: Update #1 starting
2012-03-09 10:11:32 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 10:11:34 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 10:11:34 fbuntu.py:61 INFO: Ended update #1

2012-03-09 10:11:51 fbuntu.py:56 INFO: Update #2 starting
2012-03-09 10:11:51 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 10:11:52 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 10:11:52 fbuntu.py:61 INFO: Ended update #2

...

```Okay, FBuntu is working as I would expect there.

What you need to do is edit the fbuntu.py file and remove the # from the start of the line that says "self.checkers.append(legacyInboxChecker.legacyInboxChecker(self))". You'll probably then need to logout and login again.

The reason this isn't enabled by default is that it causes some problems for some people :(

---

### Post by palimmo on 2012-03-09
> **fluteflute said:**
> Okay, FBuntu is working as I would expect there.

What you need to do is edit the fbuntu.py file and remove the # from the start of the line that says "self.checkers.append(legacyInboxChecker.legacyInboxChecker(self))". You'll probably then need to logout and login again.

The reason this isn't enabled by default is that it causes some problems for some people :(

Well.. I commented that line in order to avoid OSD notifications.
Could I have a working notification only in the message menu and with the icon changing in blue? thanks!

---

### Post by fluteflute on 2012-03-09
> **palimmo said:**
> Well.. I commented that line in order to avoid OSD notifications.
Could I have a working notification only in the message menu and with the icon changing in blue? thanks!Ah. That's possible, but not all that easy. I can give you a workaround, but you could also [subscribe to this bug]("https://bugs.launchpad.net/fbuntu/+bug/950694").

As a workaround in the meantime, make sure the line I mentioned is uncommented, and replace your legacyInboxChecker.py with the following:
```
#!/usr/bin/env python
#

#
# This file is part of FBuntu.
#
# FBuntu is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# FBuntu is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Fbuntu.  If not, see <http://www.gnu.org/licenses/>.

import logging, urllib, urllib2, json, time

class legacyInboxChecker:
    def __init__(self, parent):
        self.logger = logging.getLogger(__name__)
        self.parent = parent
        self.oauth_access_token = parent.oauth_access_token
        self.messageArray = []

    def recheck(self):
        self.logger.info("Checking Facebook")
        self.retrieve()
        self.processResponse()

    def retrieve(self):
        query = "SELECT subject,snippet,snippet_author,updated_time,thread_id FROM thread WHERE folder_id = 0 AND unread != 0"
        query = urllib.quote(query)
        url = "https://api.facebook.com/method/fql.query?" + "format=json" + "&access_token=" + self.oauth_access_token + "&query=" + query

        success = 0
        while success == 0:
            try:
                self.response = json.loads(urllib2.urlopen(url,timeout=15).read())
            except urllib2.HTTPError, e:
                self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
                time.sleep(15)
            except urllib2.URLError, e:
                self.logger.warning("We failed to reach a server. Reason: %s" % (e.reason))
                time.sleep(15)
            except IOError, e:
                self.logger.warning("IOError. More info: %s" % (e))
                time.sleep(15)
            except Exception, e:
                self.logger.warning("Exception. More info: %s" % (e))
                time.sleep(15)                
            else:
                success = 1

        try:
            self.response['error_code']
        except:
            pass # good news, we haven't found an error code
        else:
            self.logger.error("Error %s %s" % (self.response['error_code'], self.response['error_msg']))
            import sys
            sys.exit()

        self.logger.debug(self.response)

    def processResponse(self):

        # checks each message system knows, to see if still considered unread by fb
        for inboxMessageInArray in self.messageArray:
            snapped = False
            for response in self.response:
                if response['thread_id'] == inboxMessageInArray.response['thread_id']:
                    snapped = True # message still unread
                    self.logger.debug("%s is still unread" % (inboxMessageInArray.response['thread_id']))
            if snapped == False: # message no longer unread
                self.logger.debug("%s is no longer unread" % (inboxMessageInArray.response['thread_id']))
                inboxMessageInArray.indicator.hide()
                self.messageArray.remove(inboxMessageInArray)

        # check each message in response against array
        for response in self.response:

            # skip thread if in blacklist (see https://answers.launchpad.net/fbuntu/+faq/1772)
            # this is just an example of the format of a blacklist
            blacklist = ['2040095356132', '1981718745732', 't_hQvKmvIIpOwByHHhUniOKA', '2220209462240', '2158909489034', '2380320350111']
            if response['thread_id'] in blacklist:
                self.logger.debug("Skipping thread %s because it is blacklisted, see https://answers.launchpad.net/fbuntu/+faq/1772" % (response['thread_id']))
                continue

            threadAlreadyKnown = False

            for arrayInboxMessage in self.messageArray:
                if response['thread_id'] == arrayInboxMessage.response['thread_id']:
                    index = self.messageArray.index(arrayInboxMessage)
                    self.logger.debug("Already know about thread %s - in messageArray at index %d" % (response['thread_id'], index))
                    threadAlreadyKnown = True
                    self.messageArray[index].update(response)

            if threadAlreadyKnown == False:
                self.logger.debug("Thread %s not previously known about" % (response['thread_id']))
                self.messageArray.append(inboxMessage(self,response))

import indicate, pynotify

class inboxMessage():
    def __init__(self, parent, message):
        self.parent = parent

        self.response = message

        self.indicator = indicate.Indicator()
        self.indicator.set_property("subtype", "im")
        self.indicator.connect("user-display", self.mmClicked)
        self.indicator.set_property("draw-attention", "true")
        self.update(message, True)
        self.indicator.show()

    def update(self, message, forceUpdate=False):
        if (message != self.response) or (forceUpdate == True):
            self.response = message
            self.mmUpdate()


    def mmUpdate(self):
        mmText = self.parent.parent.nameFromId(self.response['snippet_author']) + " sent you a message"
        self.indicator.set_property("sender", mmText)
        self.indicator.set_property_time("time", int(self.response['updated_time']))
        self.website = "http://facebook.com"

    def mmClicked(self, a, b):
        # a is the same as self.indicator
        # b is an integer, likely time of sort sort
        import webbrowser
        webbrowser.open(self.website)
        self.indicator.hide()
        self.parent.logger.info("Deleting thread %s because clicked on.\n" % (self.response['thread_id']))
        self.parent.messageArray.remove(self) # remove ourself from our parent's array
```

---

### Post by palimmo on 2012-03-09
> **fluteflute said:**
> Ah. That's possible, but not all that easy. I can give you a workaround, but you could also [subscribe to this bug]("https://bugs.launchpad.net/fbuntu/+bug/950694").

As a workaround in the meantime, make sure the line I mentioned is uncommented, and replace your legacyInboxChecker.py with the following:
```
#!/usr/bin/env python
#

#
# This file is part of FBuntu.
#
# FBuntu is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# FBuntu is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Fbuntu.  If not, see <http://www.gnu.org/licenses/>.

import logging, urllib, urllib2, json, time

class legacyInboxChecker:
    def __init__(self, parent):
        self.logger = logging.getLogger(__name__)
        self.parent = parent
        self.oauth_access_token = parent.oauth_access_token
        self.messageArray = []

    def recheck(self):
        self.logger.info("Checking Facebook")
        self.retrieve()
        self.processResponse()

    def retrieve(self):
        query = "SELECT subject,snippet,snippet_author,updated_time,thread_id FROM thread WHERE folder_id = 0 AND unread != 0"
        query = urllib.quote(query)
        url = "https://api.facebook.com/method/fql.query?" + "format=json" + "&access_token=" + self.oauth_access_token + "&query=" + query

        success = 0
        while success == 0:
            try:
                self.response = json.loads(urllib2.urlopen(url,timeout=15).read())
            except urllib2.HTTPError, e:
                self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
                time.sleep(15)
            except urllib2.URLError, e:
                self.logger.warning("We failed to reach a server. Reason: %s" % (e.reason))
                time.sleep(15)
            except IOError, e:
                self.logger.warning("IOError. More info: %s" % (e))
                time.sleep(15)
            except Exception, e:
                self.logger.warning("Exception. More info: %s" % (e))
                time.sleep(15)                
            else:
                success = 1

        try:
            self.response['error_code']
        except:
            pass # good news, we haven't found an error code
        else:
            self.logger.error("Error %s %s" % (self.response['error_code'], self.response['error_msg']))
            import sys
            sys.exit()

        self.logger.debug(self.response)

    def processResponse(self):

        # checks each message system knows, to see if still considered unread by fb
        for inboxMessageInArray in self.messageArray:
            snapped = False
            for response in self.response:
                if response['thread_id'] == inboxMessageInArray.response['thread_id']:
                    snapped = True # message still unread
                    self.logger.debug("%s is still unread" % (inboxMessageInArray.response['thread_id']))
            if snapped == False: # message no longer unread
                self.logger.debug("%s is no longer unread" % (inboxMessageInArray.response['thread_id']))
                inboxMessageInArray.indicator.hide()
                self.messageArray.remove(inboxMessageInArray)

        # check each message in response against array
        for response in self.response:

            # skip thread if in blacklist (see https://answers.launchpad.net/fbuntu/+faq/1772)
            # this is just an example of the format of a blacklist
            blacklist = ['2040095356132', '1981718745732', 't_hQvKmvIIpOwByHHhUniOKA', '2220209462240', '2158909489034', '2380320350111']
            if response['thread_id'] in blacklist:
                self.logger.debug("Skipping thread %s because it is blacklisted, see https://answers.launchpad.net/fbuntu/+faq/1772" % (response['thread_id']))
                continue

            threadAlreadyKnown = False

            for arrayInboxMessage in self.messageArray:
                if response['thread_id'] == arrayInboxMessage.response['thread_id']:
                    index = self.messageArray.index(arrayInboxMessage)
                    self.logger.debug("Already know about thread %s - in messageArray at index %d" % (response['thread_id'], index))
                    threadAlreadyKnown = True
                    self.messageArray[index].update(response)

            if threadAlreadyKnown == False:
                self.logger.debug("Thread %s not previously known about" % (response['thread_id']))
                self.messageArray.append(inboxMessage(self,response))

import indicate, pynotify

class inboxMessage():
    def __init__(self, parent, message):
        self.parent = parent

        self.response = message

        self.indicator = indicate.Indicator()
        self.indicator.set_property("subtype", "im")
        self.indicator.connect("user-display", self.mmClicked)
        self.indicator.set_property("draw-attention", "true")
        self.update(message, True)
        self.indicator.show()

    def update(self, message, forceUpdate=False):
        if (message != self.response) or (forceUpdate == True):
            self.response = message
            self.mmUpdate()


    def mmUpdate(self):
        mmText = self.parent.parent.nameFromId(self.response['snippet_author']) + " sent you a message"
        self.indicator.set_property("sender", mmText)
        self.indicator.set_property_time("time", int(self.response['updated_time']))
        self.website = "http://facebook.com"

    def mmClicked(self, a, b):
        # a is the same as self.indicator
        # b is an integer, likely time of sort sort
        import webbrowser
        webbrowser.open(self.website)
        self.indicator.hide()
        self.parent.logger.info("Deleting thread %s because clicked on.\n" % (self.response['thread_id']))
        self.parent.messageArray.remove(self) # remove ourself from our parent's array
```

I did it. Soon I'll see if it works.

```
2012-03-09 12:17:40 fbuntu.py:56 INFO: Update #1 starting
2012-03-09 12:17:40 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 12:17:41 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 12:17:41 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-09 12:17:44 legacyInboxChecker.py:67 DEBUG: []
2012-03-09 12:17:44 fbuntu.py:61 INFO: Ended update #1

2012-03-09 12:17:59 fbuntu.py:56 INFO: Update #2 starting
2012-03-09 12:17:59 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 12:18:00 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 12:18:00 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-09 12:18:02 legacyInboxChecker.py:67 DEBUG: []
2012-03-09 12:18:02 fbuntu.py:61 INFO: Ended update #2

2012-03-09 12:18:19 fbuntu.py:56 INFO: Update #3 starting
2012-03-09 12:18:19 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 12:18:20 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 12:18:20 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-09 12:18:23 legacyInboxChecker.py:67 DEBUG: []
2012-03-09 12:18:23 fbuntu.py:61 INFO: Ended update #3

2012-03-09 12:18:39 fbuntu.py:56 INFO: Update #4 starting
2012-03-09 12:18:39 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-09 12:18:40 graphNotificationChecker.py:38 DEBUG: []
2012-03-09 12:18:40 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-09 12:18:42 legacyInboxChecker.py:67 DEBUG: []
2012-03-09 12:18:42 fbuntu.py:61 INFO: Ended update #4
```

---

### Post by palimmo on 2012-03-11
Well... I like very much this app.
Regarding the OSD, I think (but I'm not sure) that now OSD notifications are disabled for private messages... but still active for general notifications.
That's not too bad.... however, can I disable them?

---

### Post by fluteflute on 2012-03-11
> **palimmo said:**
> Well... I like very much this app.
Regarding the OSD, I think (but I'm not sure) that now OSD notifications are disabled for private messages... but still active for general notifications.
That's not too bad.... however, can I disable them?You're absolutely right.

Replace the graphNotificationChecker.py file with the following:
```
#!/usr/bin/env python
#
# Copyright (C) 2011 
#
# This file is part of FBuntu.
#
# FBuntu is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# FBuntu is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Fbuntu.  If not, see <http://www.gnu.org/licenses/>.

import logging, urllib, urllib2, json, time

class graphNotificationChecker:
    def __init__(self, parent):
        self.logger = logging.getLogger(__name__)
        self.parent = parent
        self.oauth_access_token = parent.oauth_access_token
        self.notificationArray = []
        self.graph = parent.graph
        self.user = self.graph.get_object("me")

    def recheck(self):
        self.logger.info("Checking Facebook")
        self.retrieve()
        self.processResponse()

    def retrieve(self):
        self.response = self.graph.get_connections(self.user["id"], "notifications")['data']
        self.logger.debug(self.response)

    def processResponse(self):

        # checks each message system knows, to see if still considered unread by fb
        for notificationInArray in self.notificationArray:
            snapped = False
            for response in self.response:
                if response['id'] == notificationInArray.response['id']:
                    snapped = True # message still unread
                    self.logger.debug("%s is still unread" % (notificationInArray.response['id']))
            if snapped == False: # message no longer unread
                self.logger.debug("%s is no longer unread" % (notificationInArray.response['id']))
                notificationInArray.indicator.hide()
                self.notificationArray.remove(notificationInArray)
        # check each message in response against array
        for response in self.response:
            notificationAlreadyKnown = False

            for arrayNotification in self.notificationArray:
                if response['id'] == arrayNotification.response['id']:
                    index = self.notificationArray.index(arrayNotification)
                    self.logger.debug("Already know about notification %s - in notificationArray at index %d" % (response['id'], index))
                    notificationAlreadyKnown = True
                    self.notificationArray[index].update(response)

            if notificationAlreadyKnown == False:
                self.logger.debug("Notification %s not previously known about" % (response['id']))
                self.notificationArray.append(notification(self, response))

import indicate, pynotify

class notification():
    def __init__(self, parent, notification):
        self.parent = parent
        self.response = notification

        if not 'message' in self.response:
            self.response['message'] = ""
        if not 'link' in self.response:
            self.response['link'] = "http://facebook.com"

        self.indicator = indicate.Indicator()
        self.indicator.set_property("subtype", "im")
        self.indicator.connect("user-display", self.mmClicked)
        self.indicator.set_property("draw-attention", "true")
        self.update(notification, True)
        self.indicator.show()

    def update(self, notification, forceUpdate=False):
        if (notification['updated_time'] != self.response['updated_time']) or (forceUpdate == True):        
            self.response = notification
            if not 'message' in self.response:
                self.response['message'] = ""
            if not 'link' in self.response:
                self.response['link'] = "http://facebook.com"
            self.image = self.parent.parent.pictureFromId(self.response['from']['id'])
            self.mmUpdate()

    def mmUpdate(self):
        mmText = self.response['title']
        self.indicator.set_property("sender", mmText)
        import dateutil.parser
        dt = dateutil.parser.parse(self.response['updated_time'])
        self.indicator.set_property_time("time", int(dt.strftime("%s")))
        self.website = self.response['link']

        if not self.image == None:
            import gtk
            #convert the imge to a pixbuf
            pixbuf=gtk.gdk.pixbuf_new_from_file(self.image)
            self.indicator.set_property_icon("icon", pixbuf)

    def mmClicked(self, a, b):
        # a is the same as self.indicator
        # b is an integer, likely time of sort sort
        import webbrowser
        webbrowser.open(self.website)
        self.indicator.hide()
        self.parent.logger.info("Deleting notification %s because clicked on.\n" % (self.response['id']))
        self.parent.notificationArray.remove(self) # remove ourself from our parent's array
```

---

### Post by palimmo on 2012-03-12
Excellent! thanks!
I think you should write this in the readme file.... or explain how to do it.

---

### Post by Rasa1111 on 2012-03-12
> **fluteflute said:**
> A little. I update it to fit my needs basically... I'm well aware that it's not perfect.

Are you using it?


No, I tried to download/install it, but nothing happened and it's nowhere to be seen. :/

---

### Post by fluteflute on 2012-03-12
> **Rasa1111 said:**
> No, I tried to download/install it, but nothing happened and it's nowhere to be seen. :/Hmm, how did you try to install?

Do you have a ~/.fbuntu/bin/debug.log file? If so, could you copy and paste it's contents here?

---

### Post by shizz on 2012-03-12
Really love this app. I was wondering if you could explain what you are telling him to do here? I can't follow what he was giving out about.
> **fluteflute said:**
> You're absolutely right.

Replace the graphNotificationChecker.py file with the following:.....


I did notice one thing though. If someone posts on my wall that has a long name, or it tells me that "this and that person wrote on your wall" it makes the messaging menu very big. Its not that big of a problem but it would be good if notifications over a certain length are capped and replaced with ... to show they continue.

Apart from that no problems so far. Well done.

---

### Post by Rasa1111 on 2012-03-12
> **fluteflute said:**
> Hmm, how did you try to install?

Do you have a ~/.fbuntu/bin/debug.log file? If so, could you copy and paste it's contents here?


per these instructions~ [http://www.webupd8.org/2011/07/fbuntu-facebook-notifier-with-ubuntu.html](http://www.webupd8.org/2011/07/fbuntu-facebook-notifier-with-ubuntu.html)

Could not find that file. 

Just tried to install again, 
and after the ```
 bzr branch lp:fbuntu 
``` line, 
I get 
> @ahmose-ThinkPad-Z61t:~$ bzr branch lp:fbuntu
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Target directory "fbuntu" already exists. 

am I just missing a step, or confused, or what? 

grr!

---

### Post by Rasa1111 on 2012-03-13
found debug.log~ 
> 2012-03-12 19:59:57 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:00:13 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:00:29 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:00:45 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:01:08 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:01:24 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:01:40 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:01:56 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:02:12 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:02:28 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:02:44 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:03:00 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:03:16 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400
2012-03-12 20:03:31 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400

---

### Post by palimmo on 2012-03-15
Is it possible to set how frequently should the app look for updates in my account?
thanks!

---

### Post by fluteflute on 2012-03-15
> **palimmo said:**
> Is it possible to set how frequently should the app look for updates in my account?
thanks!Yes, in the fbuntu.py file, scroll down to the second to last line. Change the *20* to some other value (measured in seconds).

---

### Post by palimmo on 2012-03-15
> **fluteflute said:**
> Yes, in the fbuntu.py file, scroll down to the second to last line. Change the *20* to some other value (measured in seconds).

Excellent! Thanks!

---

### Post by Rasa1111 on 2012-03-15
Suppose I should just give up on it. lol :/

---

### Post by fluteflute on 2012-03-16
> **Rasa1111 said:**
> Suppose I should just give up on it. lol :/Is the same message still appearing at the bottom of your debug.log (e.g. with today's date)?

---

### Post by Rasa1111 on 2012-03-16
Nah, Hasnt changed..
last line is- 
> 2012-03-12 20:03:31 facebook.py:178 WARNING: The server couldn't fulfill the request. Error code: 400

I dunno wth's going on. :/

---

### Post by fluteflute on 2012-03-17
> **Rasa1111 said:**
> Nah, Hasnt changed..
last line is- 


I dunno wth's going on. :/The 2012-03-**12** shows that is from four/five days ago.

It would be good if you could try running the program again. Trying running "python ~/.fbuntu/bin/fbuntu.py" at a terminal, and then see what happens to your debug file.

---

### Post by palimmo on 2012-03-17
Today it doesn't show a notification (a friend of mine commented on his own status.... where I posted yesterday)

```
2012-03-17 17:17:50 facebook.py:181 WARNING: We failed to reach a server. Reason: [Errno -2] Name or service not known
2012-03-17 17:18:05 facebook.py:181 WARNING: We failed to reach a server. Reason: [Errno -2] Name or service not known
2012-03-17 17:18:23 fbuntu.py:56 INFO: Update #1 starting
2012-03-17 17:18:23 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:18:24 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:18:24 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:18:27 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:18:27 fbuntu.py:61 INFO: Ended update #1

2012-03-17 17:20:22 fbuntu.py:56 INFO: Update #2 starting
2012-03-17 17:20:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:20:24 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:20:24 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:20:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:20:26 fbuntu.py:61 INFO: Ended update #2

2012-03-17 17:22:22 fbuntu.py:56 INFO: Update #3 starting
2012-03-17 17:22:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:22:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:22:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:22:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:22:26 fbuntu.py:61 INFO: Ended update #3

2012-03-17 17:24:22 fbuntu.py:56 INFO: Update #4 starting
2012-03-17 17:24:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:24:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:24:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:24:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:24:26 fbuntu.py:61 INFO: Ended update #4

2012-03-17 17:26:22 fbuntu.py:56 INFO: Update #5 starting
2012-03-17 17:26:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:26:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:26:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:26:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:26:26 fbuntu.py:61 INFO: Ended update #5

2012-03-17 17:28:22 fbuntu.py:56 INFO: Update #6 starting
2012-03-17 17:28:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:28:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:28:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:28:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:28:26 fbuntu.py:61 INFO: Ended update #6

2012-03-17 17:30:22 fbuntu.py:56 INFO: Update #7 starting
2012-03-17 17:30:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:30:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:30:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:30:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:30:26 fbuntu.py:61 INFO: Ended update #7

2012-03-17 17:32:22 fbuntu.py:56 INFO: Update #8 starting
2012-03-17 17:32:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:32:24 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:32:24 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:32:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:32:26 fbuntu.py:61 INFO: Ended update #8

2012-03-17 17:34:22 fbuntu.py:56 INFO: Update #9 starting
2012-03-17 17:34:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:34:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:34:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:34:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:34:26 fbuntu.py:61 INFO: Ended update #9

2012-03-17 17:36:22 fbuntu.py:56 INFO: Update #10 starting
2012-03-17 17:36:22 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-03-17 17:36:23 graphNotificationChecker.py:38 DEBUG: []
2012-03-17 17:36:23 legacyInboxChecker.py:30 INFO: Checking Facebook
2012-03-17 17:36:26 legacyInboxChecker.py:67 DEBUG: []
2012-03-17 17:36:26 fbuntu.py:61 INFO: Ended update #10
```

---

### Post by shizz on 2012-03-17
> **shizz said:**
> Really love this app. I was wondering if you could explain what you are telling him to do here? I can't follow what he was giving out about.


I did notice one thing though. If someone posts on my wall that has a long name, or it tells me that "this and that person wrote on your wall" it makes the messaging menu very big. Its not that big of a problem but it would be good if notifications over a certain length are capped and replaced with ... to show they continue.

Apart from that no problems so far. Well done.

Any chance you could comment on this? Or if you could tell me how I could change it?

I understand if you are busy.

---

### Post by Rasa1111 on 2012-03-17
> **fluteflute said:**
> The 2012-03-**12** shows that is from four/five days ago.

It would be good if you could try running the program again. Trying running "python ~/.fbuntu/bin/fbuntu.py" at a terminal, and then see what happens to your debug file.


in terminal I get. ```
ahmose@ahmose-ThinkPad-Z61t:~$ python ~/.fbuntu/bin/fbuntu.py
python: can't open file '/home/ahmose/.fbuntu/bin/fbuntu.py': [Errno 2] No such file or directory
ahmose@ahmose-ThinkPad-Z61t:~$ 

```

degug log hasnt changed at all. O_o

---

### Post by jimmygoska on 2012-04-27
Hello!

Just tried installing this and am getting an error when I start it:

$ python ~/fbuntu/fbuntu.py 
Traceback (most recent call last):
  File "/home/james/fbuntu/fbuntu.py", line 21, in <module>
    import notificationChecker, unifiedInboxChecker, legacyInboxChecker, graphNotificationChecker
  File "/home/james/fbuntu/notificationChecker.py", line 93, in <module>
    import indicate, pynotify
ImportError: No module named indicate

Any ideas? There's also no debug.log file anywhere.

Cheers,

James

---

### Post by fluteflute on 2012-04-28
> **jimmygoska said:**
> Hello!

Just tried installing this and am getting an error when I start it:

$ python ~/fbuntu/fbuntu.py 
Traceback (most recent call last):
  File "/home/james/fbuntu/fbuntu.py", line 21, in <module>
    import notificationChecker, unifiedInboxChecker, legacyInboxChecker, graphNotificationChecker
  File "/home/james/fbuntu/notificationChecker.py", line 93, in <module>
    import indicate, pynotify
ImportError: No module named indicate

Any ideas? There's also no debug.log file anywhere.

Cheers,

JamesI think that problem will be fixed if you install the python-indicate package (you can do this from the Software Centre or using apt-get).

---

### Post by jimmygoska on 2012-04-28
> **fluteflute said:**
> I think that problem will be fixed if you install the python-indicate package (you can do this from the Software Centre or using apt-get).

Hey, thanks for the reply, I'll give that a go when I'm next on that computer. Today I tried getting it to run on a different machine but got this error:

```
2012-04-28 18:47:03 fbuntu.py:55 INFO: Update #2 starting
2012-04-28 18:47:03 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-04-28 18:47:04 fbuntu.py:139 ERROR: Traceback (most recent call last):
  File "./fbuntu.py", line 58, in update
    checker.recheck()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 33, in recheck
    self.retrieve()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 37, in retrieve
    self.response = self.graph.get_connections(self.user["id"], "notifications")['data']
  File "/home/james/fbuntu/facebook.py", line 108, in get_connections
    return self.request(id + "/" + connection_name, args)
  File "/home/james/fbuntu/facebook.py", line 263, in request
    self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
AttributeError: 'GraphAPI' object has no attribute 'logger'
```

Sorry, I'm not very good at this debugging... :confused:

Cheers,

James

---

### Post by fluteflute on 2012-04-29
> **jimmygoska said:**
> Hey, thanks for the reply, I'll give that a go when I'm next on that computer. Today I tried getting it to run on a different machine but got this error:

```
2012-04-28 18:47:03 fbuntu.py:55 INFO: Update #2 starting
2012-04-28 18:47:03 graphNotificationChecker.py:32 INFO: Checking Facebook
2012-04-28 18:47:04 fbuntu.py:139 ERROR: Traceback (most recent call last):
  File "./fbuntu.py", line 58, in update
    checker.recheck()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 33, in recheck
    self.retrieve()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 37, in retrieve
    self.response = self.graph.get_connections(self.user["id"], "notifications")['data']
  File "/home/james/fbuntu/facebook.py", line 108, in get_connections
    return self.request(id + "/" + connection_name, args)
  File "/home/james/fbuntu/facebook.py", line 263, in request
    self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
AttributeError: 'GraphAPI' object has no attribute 'logger'
```

Sorry, I'm not very good at this debugging... :confused:

Cheers,

JamesSorry that's my fault - there was a bug that I fixed on my machine, but forgot to share the fix with everyone else!

If you run 'bzr update' from a terminal (whilst within the fbuntu folder) that particular error shouldn't happen again.

Thanks for bearing with me, all the information you've been providing is exactly what I need to help debug your problem.

---

### Post by jimmygoska on 2012-04-29
> **fluteflute said:**
> Sorry that's my fault - there was a bug that I fixed on my machine, but forgot to share the fix with everyone else!

If you run 'bzr update' from a terminal (whilst within the fbuntu folder) that particular error shouldn't happen again.

Thanks for bearing with me, all the information you've been providing is exactly what I need to help debug your problem.

Gave that a go but didn't seem to change anything:

```
james@james-timelineX:~$ cd fbuntu/
james@james-timelineX:~/fbuntu$ bzr update
Tree is up to date at revision 35 of branch /home/james/fbuntu
james@james-timelineX:~/fbuntu$ python fbuntu.py 
Traceback (most recent call last):
  File "fbuntu.py", line 58, in update
    checker.recheck()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 33, in recheck
    self.retrieve()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 37, in retrieve
    self.response = self.graph.get_connections(self.user["id"], "notifications")['data']
  File "/home/james/fbuntu/facebook.py", line 108, in get_connections
    return self.request(id + "/" + connection_name, args)
  File "/home/james/fbuntu/facebook.py", line 263, in request
    self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
AttributeError: 'GraphAPI' object has no attribute 'logger'
Error in sys.excepthook:
Traceback (most recent call last):
  File "fbuntu.py", line 142, in custom_exceptionHook
    os.system('zenity --info --text="My apologies.\n\nFBuntu has encountered an error.\n\nPlease see the logs for full details.\n\nFBuntu has quit."' % (value))
TypeError: not all arguments converted during string formatting
```

(Just saw you're in Soton as well, crap weather, isn't it?)

---

### Post by fluteflute on 2012-04-29
> **jimmygoska said:**
> Gave that a go but didn't seem to change anything:

```
james@james-timelineX:~$ cd fbuntu/
james@james-timelineX:~/fbuntu$ bzr update
Tree is up to date at revision 35 of branch /home/james/fbuntu
james@james-timelineX:~/fbuntu$ python fbuntu.py 
Traceback (most recent call last):
  File "fbuntu.py", line 58, in update
    checker.recheck()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 33, in recheck
    self.retrieve()
  File "/home/james/fbuntu/graphNotificationChecker.py", line 37, in retrieve
    self.response = self.graph.get_connections(self.user["id"], "notifications")['data']
  File "/home/james/fbuntu/facebook.py", line 108, in get_connections
    return self.request(id + "/" + connection_name, args)
  File "/home/james/fbuntu/facebook.py", line 263, in request
    self.logger.warning("The server couldn't fulfill the request. Error code: %s" % (e.code))
AttributeError: 'GraphAPI' object has no attribute 'logger'
Error in sys.excepthook:
Traceback (most recent call last):
  File "fbuntu.py", line 142, in custom_exceptionHook
    os.system('zenity --info --text="My apologies.\n\nFBuntu has encountered an error.\n\nPlease see the logs for full details.\n\nFBuntu has quit."' % (value))
TypeError: not all arguments converted during string formatting
```

(Just saw you're in Soton as well, crap weather, isn't it?)Hmm that says revision 35, but the latest is 37. Could you try 'bzr update' again? (I'm wondering if the new two versions take time to become available or something :S)

Yeah the weather is nasty!

---

### Post by jimmygoska on 2012-04-29
> **fluteflute said:**
> Hmm that says revision 35, but the latest is 37. Could you try 'bzr update' again? (I'm wondering if the new two versions take time to become available or something :S)

Yeah the weather is nasty!

Just tried it again and still says 35. I'll try again in a little while and see what happens. Cheers!

==============================

Edit 21:15

Tried a couple more times but still at version 35.

Would it help to delete the files and try again from the beginning?

---

### Post by jimmygoska on 2012-05-01
> **fluteflute said:**
> Hmm that says revision 35, but the latest is 37. Could you try 'bzr update' again? (I'm wondering if the new two versions take time to become available or something :S)

Yeah the weather is nasty!

Hey,

I've tried running 'bzr update' a couple more times and it still says version 35.

Cheers,

James

======================================

Edit

On the plus side I didn't have the 'python-indicate' package. Got that done but now I have the other issue on both machines.

---

### Post by funkwave on 2012-05-01
Hello! (Please, excuse my English :D) It works perfectly!

¿Do you have any idea of how to set a **sound** for those notifications?

Thanks in advance! ;)

---

### Post by fluteflute on 2012-05-16
> **jimmygoska said:**
> I've tried running 'bzr update' a couple more times and it still says version 35.
I haven't replied before now because I don't know what might be causing this!

The only thing I can think of would be to try deleting your FBuntu install, and starting from scratch. (So run "bzr branch lp:fbuntu" and you should get the text "Branched 38 revisions."

---

### Post by fluteflute on 2012-05-16
> **funkwave said:**
> Hello! (Please, excuse my English :D) It works perfectly!

¿Do you have any idea of how to set a **sound** for those notifications?

Thanks in advance! ;)

You can play a sound from the terminal using "aplay /usr/share/sounds/alsa/Front_Center.wav" (obviously replace the file by the wav/mp3/ogg/etc that you'd like to play).

The way to integrate this into FBuntu would depend a little on whether you want the sound for Inbox Messages or for Notifications. I'll give you the notifications method, but I'm sure you could work out the same idea for inbox messages.

Open the graphNotificationChecker.py file, and at around line 64 change to:
```
            if notificationAlreadyKnown == False:
                self.logger.debug("Notification %s not previously known about" % (response['id']))
                self.notificationArray.append(notification(self, response))
                os.system('aplay /usr/share/sounds/alsa/Front_Center.wav')
```

(the bottom line is the important new one)

And at the top of the file, you'll need to change to:
```
import logging, urllib, urllib2, json, time, os
```

---

### Post by funkwave on 2012-05-16
> **fluteflute said:**
> You can play a sound from the terminal using "aplay /usr/share/sounds/alsa/Front_Center.wav" (obviously replace the file by the wav/mp3/ogg/etc that you'd like to play).

The way to integrate this into FBuntu would depend a little on whether you want the sound for Inbox Messages or for Notifications. I'll give you the notifications method, but I'm sure you could work out the same idea for inbox messages.

Open the notificationChecker.py file, and at around line 91 change to 
```

            if threadAlreadyKnown == False:
                self.logger.debug("Thread %s not previously known about" % (response['thread_id']))
                self.messageArray.append(inboxMessage(self,response))
                os.system('aplay /usr/share/sounds/alsa/Front_Center.wav')
```And at the top of the file, you'll need to change to:
```
import logging, urllib, urllib2, json, time, os
```


Thanks! What a great technical service! :D  I'll try it!

---

### Post by fluteflute on 2012-05-16
> **funkwave said:**
> Thanks! What a great technical service! :D  I'll try it!My pleasure! Sorry it took so long. I've edited my post slightly, so make sure you're looking at that version when you try it :)

---

### Post by funkwave on 2012-05-16
> **fluteflute said:**
> My pleasure! Sorry it took so long. I've edited my post slightly, so make sure you're looking at that version when you try it :)

Ook! No problem :D
Thanks again!

---

### Post by jimmygoska on 2012-05-16
> **fluteflute said:**
> I haven't replied before now because I don't know what might be causing this!

The only thing I can think of would be to try deleting your FBuntu install, and starting from scratch. (So run "bzr branch lp:fbuntu" and you should get the text "Branched 38 revisions."

Cheers, it is indeed at revision 38 and working properly! Many thanks!

---

### Post by funkwave on 2012-05-16
> **fluteflute said:**
> My pleasure! Sorry it took so long. I've edited my post slightly, so make sure you're looking at that version when you try it :)

It works for notifications (graphNotificationChecker.py) and messages (legacyInboxChecker.py) :D

Thanks,
Antonio

---

### Post by shizz on 2012-05-19
Hey man, I was wondering if there is a way to limit how long the notification is? For instance There are some groups on facebook that have really long names and it makes the notifications bar really big and pushes it to one side of the screen. I'd be interested in trying to fix this myself but I don't know really where to start?

I was thinking would it be as easy as finding the notification variable, check to see the length of the string and if it is above a certain limit cut it down to a certain length followed by "..." for instance?

---

### Post by fluteflute on 2012-05-20
> **shizz said:**
> Hey man, I was wondering if there is a way to limit how long the notification is? For instance There are some groups on facebook that have really long names and it makes the notifications bar really big and pushes it to one side of the screen. I'd be interested in trying to fix this myself but I don't know really where to start?

I was thinking would it be as easy as finding the notification variable, check to see the length of the string and if it is above a certain limit cut it down to a certain length followed by "..." for instance?

Because we're talking about notifications, you want the graphNotificationChecker.py file. 

Line 100 says *mmText = self.response['title']*. This is the line that sets the text to be displayed in the messaging menu. Change that to *mmText = self.response['title'][0:40]* (change the 40 to anything you like).

Oh and if you want three dots afterwards, you'll need append that. So change the line to *mmText = self.response['title'][0:40] + "..."*. Although that will add three dots whether or not the text has actually been chopped. I'll leave the full solution as a challenge for you to figure out ;) (But do ask if you can't work it out.)

---

### Post by shizz on 2012-05-20
> **fluteflute said:**
> Because we're talking about notifications, you want the graphNotificationChecker.py file. 

Line 100 says *mmText = self.response['title']*. This is the line that sets the text to be displayed in the messaging menu. Change that to *mmText = self.response['title'][0:40]* (change the 40 to anything you like).

Oh and if you want three dots afterwards, you'll need append that. So change the line to *mmText = self.response['title'][0:40] + "..."*. Although that will add three dots whether or not the text has actually been chopped. I'll leave the full solution as a challenge for you to figure out ;) (But do ask if you can't work it out.)

Thanks man that was a lot more than I was expecting haha is mmText the name of the variable? Also is it stored as a matrix of sorts and you are limiting the columns to 40? Just trying to get my head around it. Haven't really done python. So could I do an if loop to check if mmText has > 40 columns then *mmText = self.response['title'][0:40] + "..."* else the normal way?

---

### Post by GWBouge on 2012-05-20
Python doesn't really require you to specify data types or begin variable names with special characters, it just kindof figures it out on the fly by what you set to it.  Yeah, mmText is the variable that contains what is shown.  self.response is a dictionary (in Python speak), which contains the 'title' info you want to display.

self.response['title'] is a string, hence mmText will be a string, but you can slice strings apart like you can with lists/arrays, so:

```

# To get the first twenty characters and add ' ...'
mmText = self.response['title'][:20] + ' ...'

# slightly more elaborate: put an ellipsis between the first and last ten chars
mmText = '%s ... %s' % (self.response['title'][:10], self.response['title'][-10:])

```

So, yeah, just throw an if statement in there to see if the string is over a certain length so you can cut it up however you want, else show it all.

---

### Post by shizz on 2012-05-20
Thanks for all the help guys! I'll give it a go when I get the time.

---

### Post by zniavre on 2012-10-23
good evening 
 
Sadly this simple (but usefull) applications is broken since the 12.10 upgrade.

it does not show icon on messaging menu any more but sometimes notifications works

any update are in progress ?

[http://paste.ubuntu-fr-secours.org/src-109527](http://paste.ubuntu-fr-secours.org/src-109527)


here is the debug.log file if it can help

Best regards

---

### Post by fluteflute on 2012-10-23
> **zniavre said:**
> good evening 
 
Sadly this simple (but usefull) applications is broken since the 12.10 upgrade.

it does not show icon on messaging menu any more but sometimes notifications works

any update are in progress ?

[http://paste.ubuntu-fr-secours.org/src-109527](http://paste.ubuntu-fr-secours.org/src-109527)


here is the debug.log file if it can help

Best regardsI am aware. Unforunately at the moment I don't have the time to fix it, although I expect I will sometime (but perhaps not until Christmas :()

---

### Post by zniavre on 2012-10-24
thank you, happy to see you will continue the software

best regards

---

### Post by darkcarnivalink on 2013-02-03
Not sure if this is still active or not, but tried everything and debug file shows
"2013-02-03 09:32:40 notificationChecker.py:57 ERROR: Error 104 Requires valid signature"
nothing shows in the notification and it's wonk. I am fairly new to Ubuntu and writing this code, I am stuck in something about a SSH id for launchpad, (not too sure why I need that) but still. Have tried this got it in and loaded, followed the read me and ... nothing. Is this another dead notifier for FB?):P

---

### Post by fluteflute on 2013-02-03
> **darkcarnivalink said:**
> Is this another dead notifier for FB?):PYes sorry :p

---

### Post by darkcarnivalink on 2013-02-05
Thanks for the respond, ugh, ok well hopefully I'll find or stumble upon one that is actually working along with Google voice. Got the skype wrap around working perfectly in notifier, and the gmail notifier, be great to have all of them in one nice nifty spot since I refuse to run windows anymore after the last crash lost everything on my hd. Thanks for all the work you put in.

---

### Post by manoynmonic on 2013-04-11
It may be dead, but works great on 12.04.  Thank you for your hard work.  This is just what I was looking for.

BTW, the default settings have the notification taking about half of my screen (netbook).  Changing this line made it just right:

```
 mmText = self.response['title'][:15] + ' ...'
```

---

### Post by urwa2 on 2013-08-01
Hi, 
i followed a tutorial to install fbuntu.. but when i run the last command python ~/fbuntu/fbuntu.py I get this error.
Traceback (most recent call last):
  File "/home/urwa/fbuntu/fbuntu.py", line 21, in <module>
    import unifiedInboxChecker, legacyInboxChecker, graphNotificationChecker
  File "/home/urwa/fbuntu/unifiedInboxChecker.py", line 98, in <module>
    import indicate, pynotify
ImportError: No module named indicate

Any help would be appreciated.

---

