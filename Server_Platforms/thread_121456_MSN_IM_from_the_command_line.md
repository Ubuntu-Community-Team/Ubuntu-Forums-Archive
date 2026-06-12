---
title: "MSN IM from the command line"
date: 2006-01-25
forum: Server Platforms
---

### Post by richard42 on 2006-01-25
I'd like to be able to send MSN IM messages from the command line in Linux. Does anyone know how to do this? I've tried googling it but to no avail.

Cheers,
Richard

---

### Post by Neg127 on 2006-01-25
Freshmeat lists several cli clients for msn.

[FreshMeat Search]("http://freshmeat.net/search/?q=MSN&section=projects&Go.x=0&Go.y=0")

take alook from the link and take your pick.

---

### Post by TheHilikus on 2008-01-15
i would like to revive this thread. i would like to know the same thing. i think the answer given was not what was asked, at least not for me. I would like a way to send a message from a command shell, i DON'T want a command line CLIENT
there are a couple of CLI MSN clients out there but they take care of everything, displaying your contact list, opening new conversation, etc. i want something to send just a message to a user, like sendxmpp does for jabber
i tried using jabber and an msn module but sendxmpp doesn't like the module. if i use a real xmpp client i get the message on MSN, but from sendxmpp it doesn't work

any help will be appreciated

---

### Post by TheHilikus on 2008-01-18
ok, i have a complete solution using python and pymsn [http://telepathy.freedesktop.org/wiki/Pymsn](http://telepathy.freedesktop.org/wiki/Pymsn)

i wrote the script based on the sample script provided in the lib

```

#!/usr/bin/env python

#Author: Alejandro Endo
#Date: 18/01/08
#Description: Sends an online or offline message to an MSN account
#Libraries: Using pymsn, available here http://telepathy.freedesktop.org/wiki/Pymsn

####Imports####
import pymsn
import pymsn.event
import sys

import logging
import gobject

logging.basicConfig(level=logging.ERROR)


####Constants####
SENDER_ACCOUNT = "XXXX@hotmail.com"
SENDER_PASSWORD = "XXXX"
RECEIVER_ACCOUNT = "XXX@hotmail.com"
MESSENGER_NICK = "Roboto"
RECEIVER_NICK = "Hilikus"

###Classes####

class ClientEvents(pymsn.event.ClientEventInterface):
    def on_client_state_changed(self, state):
        if state == pymsn.event.ClientState.CLOSED:
            self._client.quit()
        elif state == pymsn.event.ClientState.OPEN:
            self._client.profile.display_name = MESSENGER_NICK
            self._client.profile.presence = pymsn.Presence.ONLINE
            self._client.profile.current_media = ("I listen to", "Master " + RECEIVER_NICK )
            gobject.timeout_add(500, self._client.start_conversation)

    def on_client_error(self, error_type, error):
        print "ERROR :", error_type, " ->", error



class WaitAndSend(pymsn.event.ConversationEventInterface):
    def on_conversation_user_joined(self, contact):
        self._client.send_text_message(pymsn.ConversationMessage(' '.join(sys.argv[1:])))

class Client(pymsn.Client):
    def __init__(self, account, quit, http_mode=False):
        server = ('messenger.hotmail.com', 1863)
        self.quit = quit
        self.account = account
        if http_mode:
            from pymsn.transport import HTTPPollConnection
            pymsn.Client.__init__(self, server, get_proxies(), HTTPPollConnection)
        else:
            pymsn.Client.__init__(self, server)
        self._event_handler = ClientEvents(self)
        gobject.idle_add(self._connect)

    def _connect(self):
        self.login(*self.account)
        return True

    def start_conversation(self):
        receiverContact = self.address_book.contacts.search_by_account(RECEIVER_ACCOUNT)
        if len(receiverContact) == 0:
            print RECEIVER_NICK + " not found in contact list"
            return True
        else:
            if receiverContact[0].presence == pymsn.Presence.OFFLINE:
                   self.oim_box.send_message(receiverContact[0], ' '.join(sys.argv[1:]))
            else:
                   self.conv = pymsn.Conversation(self, receiverContact)
                   self._convo_events = WaitAndSend(self.conv)
            gobject.timeout_add(4000, self.quit)
            return False




def main():
    import sys
    import getpass
    import signal

    import pymsn

    server = ('messenger.hotmail.com', 1863)
    account = SENDER_ACCOUNT
    passwd = SENDER_PASSWORD

    if "--http" in sys.argv:
        http_mode = True
        sys.argv.remove('--http')
    else:
        http_mode = False

    mainloop = gobject.MainLoop(is_running=True)

    def quit():
        mainloop.quit()

    def sigterm_cb():
        gobject.idle_add(quit)

    signal.signal(signal.SIGTERM, sigterm_cb)

    Client((account, passwd), quit, http_mode)
    while mainloop.is_running():
        try:
            mainloop.run()
        except KeyboardInterrupt:
            quit()

if __name__ == '__main__':
    main()


```


and the syntax is just
 ```
msnNotifier "hello, this is a message"
```

:grin:

---

### Post by chochem on 2008-03-08
> **TheHilikus said:**
> ok, i have a complete solution using python and pymsn [http://telepathy.freedesktop.org/wiki/Pymsn](http://telepathy.freedesktop.org/wiki/Pymsn)

i wrote the script based on the sample script provided in the lib


Thanks for your post - it looks interesting. A few questions, though:
1) I suppose this would only provide one way communication, right? I don't know any python but I take it this just logs on fires off the message and quits, or?
2) I tried using the pymsn package in the repos but the script says "No module named pymsn" - I can download the one your post is referring to but I don't know what to do with it. Any help?

---

### Post by TheHilikus on 2008-03-08
1) Yes, it is one directional. in theory you could make it work both ways but that was not my idea. You want might to check an msn bot, instead of a notifier. and yes: go online, send msg, quit

2) if the package doesnt work, look for instructions on how to install python libraries, i can't remember how to do it off the top of my head

---

### Post by chochem on 2008-03-08
ok thanks. i guess i'd have to do it myself then... learning python is on my list, it's just a matter of time :)

---

