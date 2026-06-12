---
title: "GVIM question"
date: 2011-09-12
forum: Ubuntu One (CLOSED)
---

### Post by hanna09 on 2011-09-12
[LEFT][COLOR=black][FONT=Arial]we're looking to search and replace some text using GVIM. We have to identify any " that is not preceeded AND proceeded by a comma (forgetting the ones at the beginning and end of the line). Then replace those with '[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]In terms of identiying the search string, we've got that cracked with:[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]/[^,]"[^,][/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]And in terms of replacing the text with the correction, we have got as far as:[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]:.,$s/[^,]”[^,]/’/gc[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]BUT[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]this seems to be deleting 3 characters i.e.[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial],"SHELL 1" DIAMETER","help" ,SHELL 'DIAMETER help,"help"[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]What we need is something that will make:[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial],"SHELL 1' DIAMETER","help[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]into[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial],SHELL 1'", help[/FONT][/COLOR][/LEFT]
 
 
[LEFT][COLOR=black][FONT=Arial]Many thanks for any help you can provide![/FONT][/COLOR][/LEFT]

---

