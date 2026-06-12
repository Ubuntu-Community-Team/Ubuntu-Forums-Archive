---
title: "Windows PowerShell"
date: 2008-11-24
forum: Windows
---

### Post by forexsystemprofi on 2008-11-24
Did anyone use [_Windows PowerShell_]("http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx")? Can it provide at least nearly as powerfull toolset for controlling computer and network as Linux console does?

---

### Post by AndrewTheArt on 2008-11-25
I've heard it's *very* powerful.

[http://en.wikipedia.org/wiki/Comparison_of_computer_shells](http://en.wikipedia.org/wiki/Comparison_of_computer_shells)

---

### Post by RoyalShrubber on 2008-11-28
> **forexsystemprofi said:**
> Did anyone use [_Windows PowerShell_]("http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx")? Can it provide at least nearly as powerfull toolset for controlling computer and network as Linux console does?

It uses .NET framework which means every API inside of it is accessible from powershell. Objects are passed between piped /linked commands instead of text like in most linux shells - this means using less error prone grep/parsing and escape-quote wizardry.. 

As powershell was created from scratch it also uses more uniformed naming convention for its command and parameter names that follow verb-noun pattern (unlike in unix where names are arbitrary and often abbreviated to something you can't possibly remember). 

So to me it looks more powerful than most linux shells , but I don't care as I absolutely hate shells :)

---

