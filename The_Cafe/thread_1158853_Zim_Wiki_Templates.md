---
title: "Zim Wiki Templates"
date: 2009-05-14
forum: The Cafe
---

### Post by Warpnow on 2009-05-14
Has anyone ever tried to build a Zim Wiki template that actually ouputs a readable webpage where the index is a menu?

It seems possible, though difficult.

---

### Post by Warpnow on 2009-05-14
I built one using a table and iframes. The challenge seems to be that I have to use an iframe because there is only one variable, page.body, which generates the page content for BOTH the index (links) and normal pages.

The template file generates a mini webpage with a sidebar with links. It works, but it isn't the prettiest. Plus. I hate using an iframe as it reduces scalability, but I can't think of another way to do it.

I'd love just being able to do like <td src="links.html">, but apparently tables can't handle that.

In order for this to work your index has to be called "links" in export options.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>

	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
		<title>[% TITLE %]</title>
		<meta name='Generator' content='Zim [% zim.version %]'>
		<style type='text/css'>
			a          { text-decoration: none      }
			a:hover    { text-decoration: underline }
			a:active   { text-decoration: underline }
			strike     { color: grey                }
			tt         { color: #2e3436;            }
			pre        { color: #2e3436;	        }
			h1         { text-decoration: underline;
				     color: #4e9a06             }
			h2         { color: #4e9a06             }
			h3         { color: #4e9a06             }
			h4         { color: #4e9a06             }
			h5         { color: #4e9a06             }
			span.insen { color: grey                }
		</style>
	</head>

<!-- Header -->
[% IF page.is_index %]
[% ELSE %]
[% IF prev %]
	[ <a href='[% prev.file %]'>Prev</a> ]
[% ELSE %]
	[ <span class='insen'>Prev</span> ]
[% END %]

	[ <a href='index.html'>Index</a> ]

[% IF next %]
	[ <a href='[% next.file %]'>Next</a> ]
[% ELSE %]
	[ <span class='insen'>Next</span> ]
[% END %]
<hr>
[% END %]
<!-- End Header -->



<TABLE BORDER="0" width="100%">
<TR>
<TD align="left" valign="top" width="25%">
[% IF page.is_index %]
[% ELSE %]
<IFRAME frameborder="0" marginwidth="0" marginheight="0" width="100%" height ="600" align="left" scrolling="No" SRC="[% notebook.root %]/links.html"></IFRAME>
[% END %]
</TD>

<TD valign="top">
[% IF page.is_index %]
<font align="left">
<base target="_top">
[% page.body %]
[% ELSE %]
<u>[% page.heading %]</u>
[% page.body %]

</TD>
</TR>
</TABLE>

<hr />
```

---

