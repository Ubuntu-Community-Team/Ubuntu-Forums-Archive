---
title: "Apache + OpenOffice"
date: 2008-05-29
forum: Server Platforms
---

### Post by vinceg on 2008-05-29
Hello everyone, 

Sorry for my english but i'm french ...

First I have to realized a project during my internship , this project is a converter to PDF file from the net, I thought that the best solutions would undoubtedly go through OpenOffice.

So after having fought a few hours, I managed to install OpenOffice and Xvfb.

As a way to root console logged I can convert my files via the command:

```
 ooffice-invisible-pt PDF filename-display: 1 
```
Unfortunately, when I want to re-enter this command in PHP and exec (), it does not work, I realized that just because the user was used www-data, I've looked everywhere over the Net but i'm unable to execute a shell or whatever at www-data to launch ooffice for conversion.

I thought added a condition in visudo so root launches the shell script conversion without a password but I do not know if this is really the top level security.

In addition to a test I added www-data group root, and it did not work too so I do not know if it comes from.

If I log on www-data on the server and I try to run the command ooffice, voila mistakes that I return:

>  [Java framework] Error in function createUserSettingsDocument (elements.cxx). javaldx failed!
[Java framework] Error in function createUserSettingsDocument (elements.cxx).
(process: 13781): GLib-GObject-CRITICAL **: gtype.c: 2240: initialization assertion failed, use IA__g_type_init () prior to this function

(process: 13781): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen) 'failed
InsertFromHorizontalBitmap - empty image!

(process: 13781): GLib-GObject-CRITICAL **: gtype.c: 2240: initialization assertion failed, use IA__g_type_init () prior to this function

(process: 13781): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen) 'failed 
I saw the need to make a chown-vR on the directory / root/.openoffice.org.2 but it did not solve my concern in fact.

Finally my server is a dedibox with Ubuntu 6.10 according / etc / issue

Thanks to help solve my problem.
I said that I am obliged to go through this server, and apache2 to perform the conversion.

---

### Post by pdwerryhouse on 2008-05-29
If I'm understanding you correctly, you're trying to create PDF files from a webserver?

If this is what you're trying to do, I don't think you're going to have much luck doing it with OpenOffice. You're probably better looking at one of the many libraries that are available for generating PDF files.

For example, from perl:

libpdf-api2-perl - create or modify PDF documents in Perl
libpdf-create-perl - Create PDF files

or python:

python-pypdf - PDF toolkit implemented solely in Python

or ruby:

libpdf-writer-ruby - Native Ruby library for creating PDF documents

Or maybe even something simple using html2ps and ps2pdf.

Cheers,

Paul

---

### Post by vinceg on 2008-05-29
Hello , 

In fact i don't want to create a PDF File.

First on the website , one user send a file doc,txt,odt ...
Second the server convert this file to PDF 
Finaly the server give a url to download the PDF files.


I don't know ruby , i want to program this website with LAMP .

---

