---
title: "Idea for an applications to make *nix support easier."
date: 2010-03-22
forum: The Cafe
---

### Post by undecim on 2010-03-22
I'd really like some opinions on an idea I've had for a while now.

I've noticed that a lot of support threads in the forums take a lot of time and effort to diagnose and fix simple things. Often times, it gets to be a back-and-forth between techie, newbie, and terminal, and the real time waster is the latency between the techie and the terminal.

Even on IRC, anyone helping a user has to ask the user to type commands into a terminal and then post a pastebin link. And it doesn't help that some users give up on pasting to the terminal when Ctrl + V doesn't work and just start transcribing commands manually. The fastest way to solve a problem would be an SSH shell to the system, but there are many obvious problems with that, most notably security.

I have an idea for a web application that would make this process much faster and allow more collaborative troubleshooting.

It involves a terminal inside a web browser (via a browser plugin). The terminal is viewable by anyone in the same room, and all communication is done over ubuntu's IRC channel (for the safety of many eyes watching out for malicious commands.)

Anyone helping another user this way can "suggest" a command, and that command will be added to a list of commands that the user can easily run. This suggestion mechanism would be handled over IRC with an english-like syntax. (For example: "techie: @newbie: try the command 'uname -a'") so that any malicious commands are caught by the many eyes of the IRC channel.

Also, to prevent sensitive information from being shown over the application (IP address, etc.), the user receiving support will need to click an "update" button before the text shown in the terminal is sent to anyone watching it. When the update button is pressed, a message is shown over IRC with a link to the web page with the room (so that anyone in a normal IRC client can join in if they know how to fix the problem)

A plugin would have to be used by the browser receiving support that can open a shell on the local system or over SSH (for fixing servers, etc.).

I have a few mock-ups below. One for the user interface (for the person receiving support) and one for the supporter interface (for people giving support). Hopefully, those are a little more clear on my idea.

---

### Post by slakkie on 2010-03-22
And how does the user learn from this?

Bad idea. Create an account for the other person if you trust him enough to let him access your system. This is just asking for problems. I can upload a file, do stuff, break the system, disconnect, and nothing can be done about it.

---

### Post by wojox on 2010-03-22
> **slakkie said:**
> I can upload a file, do stuff, break the system, disconnect, and nothing can be done about it.

Forkbomb comes to mind. ;)

I still think it's a shorter route to type or copy and paste into the terminal to help someone out. To paste in the terminal it's actually Ctrl+Shift+V

---

### Post by undecim on 2010-03-22
> **slakkie said:**
> And how does the user learn from this?

Bad idea. Create an account for the other person if you trust him enough to let him access your system. This is just asking for problems. I can upload a file, do stuff, break the system, disconnect, and nothing can be done about it.

Some users don't care about learning, just getting their problem solved.

Also, as for uploading files and breaking the system, one can just as easily do that over IRC. Any and all communication between users is done over IRC. This app just gets rid of the copy/paste/pastebin/post a link to the pastebin process.

---

### Post by madjr on 2010-03-23
well people here like to ditch other's ideas really fast and rarely suggest a better solution in return.

am sure the OP would like some suggestions for an "ideal-system" (we're just brainstorming people so chill, no bashing pls)

---

its not perfect, but i actually like the idea

it's a start

will add my views soon

---

### Post by juancarlospaco on 2010-03-23
Too complicated, i use Empathy's Desktop Sharing capabilities to help the peoplez :)
*why to complicate if you can share your desktop?*

---

### Post by eriktheblu on 2010-03-23
Great idea!

Couple of thoughts:
1. Have a safety rating scheme that can evaluate commands based on how much damage they could potentially do. This could be a lot of work, so you might stick with the base commands without switches, options, etc. Rather than rate these yourself, allow  the participating community to rate them.

Display the security rating next to the command with a link to a warning about the potential risk with that specific command.

You could also adjust ratings based on directory; /home would be safer to modify than /boot for example. Directory and sudo could be multipliers rather than ratings.

Ratings and warnings could be accessed live, or pushed with security patches.

2. Automatic links to man pages for suggested commands (this might aid in the learning aspect).

3. Identification of uninstalled programs. If a command is suggested and the newbie doesn't have the program installed, everyone should be made aware.

4. Ownership of suggestions. List the username of the guy who suggests a command next to the suggested command. Have an option for others in the room to endorse a suggestion. Endorsed commands will have the username of the original suggestion, and a "+*n*" where *n* is the number of techs who endorse it. Mouseover reveals their names.

5. Newbie side security settings. Tie this to item #1 to limit what suggested commands are visible to the newbie. Default setting should be high. Perhaps an automatic setting that adjusts the more time the newbie spends on his Linux box.

If a command exceeds the security level, newbie is shown a message '<user> suggested a command that exceeds your security settings' with a link to change security settings.

On the Tech side, display '<suggested command> exceeds <Newbie's> security settings.

High security settings may include a delay (say 10 seconds) to allow other techs to react to a potentially malicious command before it is communicated to the newbie. It can display a placeholder '<Tech's> suggestion is being reviewed by the room'. Another security option is to only display commands that have been endorsed by a predefined number of users.

6. An offline suggestion file format that could be linked on forums. Newbie clicks a link, it pops up in his suggested command box as unendorsed. Techs would have the option to endorse the command.

---

### Post by undecim on 2010-03-23
> **juancarlospaco said:**
> Too complicated, i use Empathy's Desktop Sharing capabilities to help the peoplez :)
*why to complicate if you can share your desktop?*

Because if we are sharing a desktop, what stops me from opening a terminal and running a fork bomb or worse? I could have some kind of cryptic command that boils down to "sudo rm -rf" and most people wouldn't think twice about entering their password for it.

Part of the reason for this application idea is that unfortunately, we cannot trust everyone, and so we have to take precautions. This is why everything is done over ubuntu IRC. Whenever someone uses the "suggest" feature, it will send the message "person: Try running '...'". If it's a malicious commmand, it will be seen, the user will be warned.

If I end up creating something like this, I will also have it automatically block known destructive commands, and cross out commands from people who get kicked. [s]Also, an "unsuggest feature.[/s] Bett yet, eriktheblu's endorsement suggestion

@eriktheblu

I like these ideas. I was already starting to think about the man-pages, and I'm still looking to make this just as safe as using the forums for support.

I also have a lot of feature ideas that I didn't put into the OP, but I'm using xmind at the moment to sort my ideas out. (I love that application!)

---

### Post by juancarlospaco on 2010-03-23
The user can stop you.

---

