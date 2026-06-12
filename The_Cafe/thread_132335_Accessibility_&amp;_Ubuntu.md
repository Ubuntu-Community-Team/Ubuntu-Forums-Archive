---
title: "Accessibility &amp; Ubuntu"
date: 2006-02-18
forum: The Cafe
---

### Post by meldra on 2006-02-18
Greetings,

A few hours ago in the IRC #ubuntu channel, a vision impaired individual asked whether if there was any word-processor type packages that were more user-friendly for vision-impaired people than OpenOffice or Abiword. This person was directed to consult the development team in the #ubuntu-devel channel about possible remedies, and was not taken seriously due to a comment he had made earlier in the #ubuntu channel.

First off, I would like to mention that I am aware of the port of Hoary to be accessible approximately a year ago, even before my involvement with Ubuntu began ([see here]("http://ubuntuforums.org/showthread.php?t=15374")). I am also aware that there is an accessibility team ([see here]("http://ubuntuforums.org/showthread.php?t=4808")) - although it does not seem to have much of a presence either in the forums or in the freenode IRC network.

I am not visually-impaired, but nonetheless believe that this issue is something that should be taken seriously. Vision impairment is something that will strike many of us eventually, and it is unfortunate that some people aquire this problem earlier than others.

As an outsider, I would like to make a few suggestions:

- Forum: I believe it would be highly beneficial for there to be a sub-forum somewhere for people to post accessibility howtos, and for interested/affected people to ask questions and offer suggestions to each other.

- IRC: This would be mainly beneficial for walk-ins, such as the individual tonight, where they can ask a question to people who can help them.

Since the catchcry of Ubuntu is '*Linux for Human Beings*', it's seems only fair that special effort is taken towards this issue and the existance of the accessibility team is an indication that this is being done. However, it seems silly that such an intitiative is such a hidden force.

I would also like to take this opportunity to acknowledge the accessibility team for all their hard work. Although I have not the need for their efforts at this time, one day, I may.

Meldra

---

### Post by bonzodog on 2006-02-18
Good point. I think more attention ought to paid to these options as they do exist in Ubuntu. Larger font's and themes etc. My wife is half blind and so she needs a larger case on all the text, which I have done.

---

### Post by UbuWu on 2006-02-18
Probably a good idea to post this to the accessibility mailing list as well:

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility](https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility)

---

### Post by meldra on 2006-02-19
[QUOTE=bonzodog]Good point. I think more attention ought to paid to these options as they do exist in Ubuntu. Larger font's and themes etc. My wife is half blind and so she needs a larger case on all the text, which I have done.[/QUOTE]

It would be nice to know what steps you took. All I know to suggest to the frustrated people who ask (a second visually-impaired person asked for help just today) is to install the gnome-accessibility-theme and gtk2-highcontrast packages. It'd be really good to have a knowledge repository of this information we can point interested people towards :)

---

### Post by Henrik on 2006-02-19
OK, I've looked at these conversations, and I think this particular instance of a) someone being a bit impatient and unfocused due to being tipsy on a saturday night, b) the common problem of it not always being easy to know where to turn with questions and requests within the Ubuntu community. Turning up in ubuntu-devel drunk on a Saturday night demanding a new feature when most devs are away is probably not going to yield the best result.

AFAICT good advice was already given in #ubuntu, namely to try the nano editor. It's very simple, has a large cursor and with the preferences for the terminal you can set the font size as large as you want.

**But there is a wider question here**, which we should probably discuss more seriously: the lack of visibility of the [accessibility team](https://wiki.ubuntu.com/Accessibility). One reason for this is that the AT (assistive technology) features in in Ubuntu really haven't been much to shout about so far. With the versions we have released do date, I would not go around evangelising the Ubuntu platform to visually impaired computer users (except for the few who are interested in development on the bleeding edge). I would be doing them a disservice; IMO they were better off staying with Windows or MacOSX.

However, with the release of 6.04 (dapper), this is about to change. We will have the key AT features like screen readers and magnifiers installed by default and even running as an option on the live CD. At that point we should start promoting Ubuntu more widely to the disabled community and get feedback from them on how well it's meeting their needs.

If we get an influx of new users with the need for these technologies it would also be helpful to have better sources of documentation and sources of support. WRT documentation, we are working on two documents that will be included on the CD itself and on help.ubuntu.com. First there is a [brief introduction to the available features](https://wiki.ubuntu.com/Accessibility/doc/Intro) and a more [extensive user guide](https://wiki.ubuntu.com/Accessibility/doc/Guide). (both need work, help is appreciated)

As for support, we have the ubuntu-accessibility mailing list and a separate #ubuntu-accessibility IRC channel. Both of these have a fairly low level of activity though, mainly because our accessibility team is just quite small still. And also, those may not be everyone's preferred mode of communication.

I think a special Assistive Technology sub-forum section would be very useful at this point, as a first point of call for new users with questions about what the possibilities are with the current software. It would be even better if a few members of the existing forum community could help out by answering basic questions. It should only take a few minutes to check out some of our existing AT applications, just to have a rough familiarity with them, and be able to help answer questions. We should also set up a FAQ in the wiki for this purpose.

I agree that we in the accessibility team are something of a 'hidden force' as you put it, but this is mainly due to our own limited capacity. The core team of active contributors is small, at 5-6 people perhaps, and we are focusing our energy on getting the features to actually work. We would love to see more involvement from the wider community. Much can be done with, testing, documentation writing and user support. We need more champions in the Forums and elsewhere :)

---

### Post by meldra on 2006-02-19
Henrik,

Thankyou for your response.

[QUOTE=Henrik]As for support, we have the ubuntu-accessibility mailing list and a separate #ubuntu-accessibility IRC channel. Both of these have a fairly low level of activity though, mainly because our accessibility team is just quite small still. And also, those may not be everyone's preferred mode of communication.[/QUOTE]

Unfortunately Henrik, I was unaware of the existance of this channel. If I was to go by the freenode channel list I would still not aware where it is. Considering most people go to freenode for #ubuntu, this is where I and presumably the majority of other users look. I could post a screenshot of the channel list of freenode, but I assure you, the channel isnt listed there.

I apologise if my previous paragraph sounded a bit narky. It wasnt intended to be. However the context of it is precisely my point. Lack of knowledge. I, as someone who is not impaired, simply do not know where to point people who are. 

Visibility is important.

Meldra

Edit: I have just realised why #ubuntu-accessibility doesnt show up in the freenode channel list. By default XChat only shows channels with 3 or more users...

---

### Post by Henrik on 2006-02-19
> Unfortunately Henrik, I was unaware of the existance of this channel. If I was to go by the freenode channel list I would still not aware where it is. Considering most people go to freenode for #ubuntu, this is where I and presumably the majority of other users look. I could post a screenshot of the channel list of freenode, but I assure you, the channel isnt listed there.
Good point. I assume you mean this list here: [https://wiki.ubuntu.com/InternetRelayChat](https://wiki.ubuntu.com/InternetRelayChat) I've now added an entry.

> Visibility is important.
Indeed. Both in terms of the project and documentation being visible to users, and also of applications and data being visible to everyone on the Ubuntu platform (which is what the original query was about). ;)

---

### Post by meldra on 2006-02-19
[QUOTE=Henrik]Good point. I assume you mean this list here: [https://wiki.ubuntu.com/InternetRelayChat](https://wiki.ubuntu.com/InternetRelayChat) I've now added an entry.[/QUOTE]

Actually, no. I wasn't. I completely forgot about that list anyway, i guess as I am not much of a wiki person.

What I had meant was the list you see through XChat. I did figure this out too... By default, XChat filters out channels with less than 3 users in them. A user would have to change this setting to show the channel, or we would to have at least 3 people in the channel at all times.

---

### Post by majikstreet on 2006-02-19
the truth is that #ubuntu isn't a very... friendly channel... There are numerous reasons to dislike it.. 

if you ever need anything, you can always come to #ubuntuforums , there are usually people there to talk to and are knoweldgable (not me...)

---

### Post by midwinter on 2006-02-19
Hm, I have always found #ubuntu to be very friendly indeed.

---

### Post by meldra on 2006-02-19
[QUOTE=midwinter]Hm, I have always found #ubuntu to be very friendly indeed.[/QUOTE]

Seconded.

Although this can depend entirely on who is active rather than idling and how you ask for help.

---

