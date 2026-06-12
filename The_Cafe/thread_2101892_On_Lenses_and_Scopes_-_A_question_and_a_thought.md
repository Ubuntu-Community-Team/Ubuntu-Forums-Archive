---
title: "On Lenses and Scopes - A question and a thought"
date: 2013-01-05
forum: The Cafe
---

### Post by Copper Bezel on 2013-01-05
Hey all. I'm a recent convert from Gnome Shell to Unity, and I've been involved in a discussion in the last few days on another forum on this Amazon search suggestions argument, which this topic is expressly not about (so let's please not go there.) It got me to look more deeply into how Lenses and Scopes work, though, and I ran into a couple of things that seemed like inconsistencies to me, so I'm curious to get some thoughts.

First off, can someone explain to me the distinction between Lenses and Scopes? I thought it was fairly straightforward - [_Scopes are search providers, while Lenses are search screens that can call on various Scopes_]("http://developer.ubuntu.com/resources/technologies/lenses-and-scopes/"). Explicitly, "This is because a Lens does not actually perform any searches itself. Instead, a Lens will have one or more Scopes which are the actual engines that do the searching for it." However, that doesn't seem strictly borne out. 
[INDENT]&#8226; The Wikipedia Lens is a search screen, but there is no corresponding Scope. It seems to have a built-in Scope instead. (Much the bother - I'd have preferred it as a scope in the main search screen; since it's a click away, it doesn't save me any time over searching from the browser. But the bit I'm asking about is just the terminology.) There is also no separate Wikipedia Scope daemon process in System Monitor.

&#8226; The shopping Lens is the opposite. It's called a Lens, but doesn't add a search screen, and instead reports returns in the home search screen. That sounds like the definition of a Scope.[/INDENT]

Second, as I said, I'm coming over from Gnome Shell, where I was used to these kinds of desktop extensions living in ~/.local rather than being installed system-wide. Obviously, it doesn't really matter where the executable lives; in fact, it makes more sense for the code to be a system-wide package installation. But because the Lenses and Scopes install system-wide and are run at startup, there's no user-specific configuration for the search that I could find. This seems like bad practice on a multi-user system. If Susan wants the Wikipedia lens active and the shopping lens disabled, and Rutherford wants the shopping lens active and doesn't care about the Wikipedia lens, there doesn't seem to be a way to make that happen. (I know that the Privacy settings can disable all remote searching for an individual user account. I'm referring to enabling individual Lenses and Scopes with remote searching turned on.)

I know that there's a lot of complaint about Unity lacking configuration, and I fully accept the response that adding configurability reduces consistent behavior and adds development cost while complicating the options presented to the user. However, Lenses and Scopes are meant to be available from third parties and are not (each individually) core features of the shell, which means that they will and should not be consistent across individual desktops; they're designed to be user-configurable. Yet, the only way I've found to disable a particular Lens or Scope is by removing the package from the system. Am I missing something (like a Dash search management screen,) or is this feature not available? (It seems like a necessary feature for design consistency.)

---

### Post by Gremlinzzz on 2013-01-06
:popcorn:If you like lenses i found 10 of the Best Unity Lenses & Scopes.
[http://www.omgubuntu.co.uk/2012/01/10-unity-lenses-scopes](http://www.omgubuntu.co.uk/2012/01/10-unity-lenses-scopes)

---

### Post by Copper Bezel on 2013-01-06
It is a very good list, although a bit outdated (the Tomboy lens is no longer available, boo) and I'll have to mess with some of those. I'm still more interested in these technical aspects right now, though. 

I like Scopes in concept, but I'm not finding a lot of them that connect to the home Lens, and I'm not sold on alternate Lenses yet. The Wikipedia Lens is an example, because I'd be more likely to use it if it was a category in the main search instead. I don't like that the current search string isn't the same across all lenses, because it means hitting Super, clicking the Lens, then typing again, which seems awkward. I'd much rather hit Super, type, then scroll or click all within the one search screen.

---

### Post by Copper Bezel on 2013-01-07
DNDTR. Apparently, while the Lens / Scope bit still seems inconsistent, user configuration of the Dash search [*is* on the table]("http://www.webupd8.org/2012/10/unity-680-released-with-option-to.html") (scroll to the end of the article,) it just hasn't been implemented yet. I don't know why this wouldn't be higher on the agenda, though.

---

