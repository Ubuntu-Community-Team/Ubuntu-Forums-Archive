---
title: "Latext links not working !"
date: 2012-12-10
forum: The Cafe
---

### Post by satyamM on 2012-12-10
Hi all,

I am creating my CV in Latex, but when I try to put any hyperlinks in Latex like 

\href{link_comes_here} {"Link appearance here"} .... ...............then it doesn't work.......

When I open the pdf file,  the link just turns black when clicked, but doesn't opens browser window for that link.........I mean what I want is that whenever I click on the link in the CV, it should open the browser window and open that link.........

Anyone having any idea what to do ??....

---

### Post by d.atanasov on 2012-12-10
Hi there, 

I assume you have put the usage of the package at the beginning of the document. Can you try to put instead of href just normal "url{link comes here }{ how to look in the pdf}". Also when you compile do you have any error massages or warnings ? 

cheers 

dinko

---

### Post by satyamM on 2012-12-10
> **d.atanasov said:**
> Hi there, 

I assume you have put the usage of the package at the beginning of the document. Can you try to put instead of href just normal "url{link comes here }{ how to look in the pdf}". Also when you compile do you have any error massages or warnings ? 

cheers 

dinko


Hey, thanks for the reply.
Yes I have put usage of package in beginning of the document. Does it matter to use package in between of document or in beginning....????

I tried to use use       \url{......}{......}         but it only works when the document is opened in browser.......I want that whenever the document is opened by adobe reader in its own Adobe reader window, not in browser, then the links should work i.e it should open a browser window........I hope you're are getting what I am trying to say......please ask wherever I am not clear

---

### Post by d.atanasov on 2012-12-10
Yep I know what you are trying to do, but I don`t know what is causing the trouble with the browser opening and I am trying to figure it out. Here is just simple code that I did know 
```

\documentclass[a4paper,10pt]{article}
\usepackage[utf8]{inputenc}
\usepackage{hyperref}
%opening
\title{Title}
\author{Author}
\begin{document}
\maketitle
\section{Section}

\href{http://ubuntuforums.org/showthread.php?t=2093429}{Link to the forum}

\end{document}
```And It works perfectly after compiling with pdflatex. Do you get any errors by compiling this ? Try it and we can see if it comes from the Latex or by the system...

cheers

---

### Post by satyamM on 2012-12-10
Well well well...

I am currently on a Ubuntu machine and here it is really NOT working...yours also didn't work.....i.e it didn't open a browser window when I clicked on the link given by your code...

BUT...when I checked the document on the windows machine(my brother's laptop)  ........guess what...... both worked, mine too and yours too.....

So there may be loophole somewhere in my Ubuntu's Adobe Reader settings/preferences......don't know what.....

 any ideas.....???

---

### Post by d.atanasov on 2012-12-10
Could you try open the document with other viewer like the default of Ubuntu ?

---

### Post by satyamM on 2012-12-10
> **d.atanasov said:**
> Could you try open the document with other viewer like the default of Ubuntu ?

Ohh yes.....!!

Both are working when I open in "Document Viewer" instead of Adobe's reader........!!....

---

### Post by d.atanasov on 2012-12-10
Then is obvious that is Adobe Reader who make this trouble. I use Okular which is also nice and as powerful as AR... Well I don`t know how to help you with AR default browser settings :( ... I hope that you can change them if you insist of using it :) 

cheers

---

### Post by satyamM on 2012-12-10
> **d.atanasov said:**
> Then is obvious that is Adobe Reader who make this trouble. I use Okular which is also nice and as powerful as AR... Well I don`t know how to help you with AR default browser settings :( ... I hope that you can change them if you insist of using it :) 

cheers


yes...I'll try to figure out what's happening......

anyways....thnx fr great help.....!!!! ):P

---

