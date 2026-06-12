---
title: "Beamer help?"
date: 2010-06-27
forum: The Cafe
---

### Post by bryncoles on 2010-06-27
Hallo folks. Not sure where to post this question, as it's not really about Ubuntu (at all, in any way, shape or form), but I'm sure someone here can help. 

Anyway, I'm writing a presentation using the Beamer package of LaTeX. I would like a specific graphic to appear on every page, at a location specified by me (the same location each time). If anyone is interested, the location I want to use is the top-right corner. 

I can get a logo to appear on each page, at a place specified by the style I've chosen to use (CambridgeUS, dove) using the command ```
\logo{\includegraphics[height=1cm]{image.jpg}}
```

This places the logo in the bottom-right corner however. Can anyone help me move this image up a little?

Cheers guys!

---

### Post by Stefan_K on 2010-06-28
Hi bryncoles,

a quick way would be be inserting some vertical space below the graphic like this:
```

\logo{\includegraphics[width=1cm,height=1cm]{test}\vspace{10pt}}
```
Stefan

---

### Post by bryncoles on 2010-06-28
Ah! That's awesome, thanks Stefan_K! A nice, simple solution (which would have taken me days to find)!

Just one more point... Sometimes this puts the logo behind some other feature of the template. Is there a way I can force the logo to appear in front of all other aspects of the slide?

---

