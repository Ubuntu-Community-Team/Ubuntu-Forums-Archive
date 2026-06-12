---
title: "Ubuntu Web IRC Client"
date: 2011-05-16
forum: Ubuntu Dev Link Forum
---

### Post by jpv89 on 2011-05-16
First of all, let me start off by saying I'm not an IRC junkie. I don't use IRC on a daily basis, although I use it a couple of times a month for help with whatever ubuntu-related trouble I'm having. This might make me an excellent person to say this.

The #ubuntu IRC channel seems to be an excellent place to get help for new and experienced users alike. It offers a convenient place for community discussion, with over a thousand users online at any given moment. Unfortunately, the amount of user activity in any channel of this size brings with it a terrible amount of clutter. With users constantly joining and leaving, JOINED and LEFT messages flood the channel, making it extremely hard to have a normal conversation.

Some statistics of the #ubuntu channel:

[LIST]
[*]1639 users were in the channel
[*]In half an hour, 419 lines were posted to the channel. That's an average of about 1 line every 4 seconds
[*]Of these lines. only 205 were actual messages people had written
[*]201 were messages of people having joined or left the channel, and the remainder were nick changes and kick messages.
[*]Only 5% of the people who joined the channel during this time used the freenode webchat at [webchat.freenode.net]("webchat.freenode.net").
[/LIST]

Although I haven't done any real research, it's easy to see that users might find it really hard to join in on conversations, simply because it's hard to keep track of it all, and might just close the IRC window never to return there again.

An easy way to join the IRC in a webbrowser is the qwebirc client hosted at webchat.freenode.net. Although a little research has shown that currently only 5% of users logging on use this client, new ubuntu users might do this more often when there's a better looking web-based IRC client around.


The last couple of days I've been pondering how to best build a user-friendly web-based IRC client, focussing on how to streamline communication and discussion in a large and overcrowded channel like #ubuntu. A couple of things have come to mind, which I'll share with you:

[LIST]
[*]First of all, JOINED and LEFT messages should be hidden by default.By hiding them, the continuous flood of useless messages will stop and make place for actual discussion.

[*]Actual messages should be indented and by that way seperated from the nicknames of the users that posted them. This will greatly improve readability for multi-line messages.

[*]There's no real use for monospaced fonts in the #ubuntu IRC channel. Multi line code should be pasted to pastebin, and it doesn't really matter for single line code. This way a font can be used that improves readability.

[*]Users should be able to "Star" or "Favourite" other users and messages, making it easier to keep track of the people you are actually having a conversation which. Users should also be able to only view messages of these "Starred" people.

[*]When a user posts multiple messages in succession, these messages should be displayed without having to show the user's nick everytime.
[/LIST]

The above points are most important, greatly increasing the user-friendliness of the IRC channel. Some other points that might make using the IRC a bit nicer:

[LIST]
[*]Integrated pastebin
[*]On-hover display of linked images
[/LIST]

What I'm looking for is someone with python / java skills to do the backend, or maybe reuse the backend of open-source Qwebirc. I can do the AJAX front-end, design, and also the php code. 

If you're interested, or just want to add to the discussion, please feel free to post here.

Joost

---

