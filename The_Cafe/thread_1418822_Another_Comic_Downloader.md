---
title: "Another Comic Downloader"
date: 2010-03-01
forum: The Cafe
---

### Post by cong06 on 2010-03-01
I was unsure if this was a good idea, but in the end just gave up for the sake of open source.

I wrote a perl script/program that goes and downloads comics, (I know, another one).
The purpose of this script is slightly different from the rest, however, because:
1) it focuses on general comics, and can work with almost any.
2) it focuses on the bandwidth of the user
3) it organizes the downloaded comics in such a way to make "comic books"

Below is the whole readme, but if you want to get an idea of how it works check out "Goals" and "Modes"

I'll post dependencies here also just for ease:
1) Perl
2) Wget
3) imagemagick

Let me know if you have any thoughts, ideas...
If you don't like it, that's fine, but there are situations that a tool like this is worthwhile.

Download: [http://www.isaaclw.com/cmcdwnlr2/](http://www.isaaclw.com/cmcdwnlr2/)


This Readme was posted on 1 March 2010 and may be out of date.
The updated readme is available at: [http://www.isaaclw.com/cmcdwnlr2/](http://www.isaaclw.com/cmcdwnlr2/)
```
'cmcdwnlr' is a Tool that parses through comic sites and
downloads new comics.
It is released under the GNU GPL:
    http://www.gnu.org/licenses/gpl-3.0.txt


TOC:
> Usage
> Goals
> Dependencies
> Modes
> Configuring
> Conf file
> 'url' expressions
> 'pic'/'next' expressions
> Acting on URLS
> Start of Downloading
> Tricks in Downloading
> End of Downloading
> Extras
> Bug Reports


==Usage==
/path/to/script [COMIC_NAME]
COMIC_NAME must be an entry in the conf file.
If COMIC_NAME is given, it will only act on that one
comic.
If it is not given, then all the comics will be checked.


==Goals==
The script is targeting those that have sporadic, or
occasional bandwidth. This means that since the program
runs for so long, it is expected to be resumable.
For example, the user must be able to kill the program,
and resume is where it left off.
It also means that as few downloads are done as possible,
to achieve the most number of downloaded comics.


==Dependencies==
-wget
-imagemagick
-perl (of course)
I considered ditching the wget dependency, but found that
wget is so much better then built in perl downloading.


==Modes==
It has two modes:
- Counting mode, where the site url or image contains an
    incrementing number
- Full Parsing mode, where the site has a "next" or "back"
    button.
Counting mode is default unless the "next" value is set in
the conf file
In Counting mode, the files are grabbed in two ways:
- Direct download.
    If the image is stored online increments, then the
    direct link to the image can be listed by itself in
    the conf file.
    This means that the "title" text (or mouse over text)
    can not be gathered.
- Indirect download.
    If the url where the image is stored incrementing
    format then a regular expression 'pic' can be set, to
    catch the image in the page.
    With this option, you can also set "get_text" in order
    to capture the title text/mouse over text of the
    image.
Counting Mode is 'cleaner' with it's output then Parsing
mode because it has more control over the naming, but
quite a bit more complicated. Sometimes comics have
missing files because they don't count perfectly. See the
'skip_ahead' option in the conf file.
In Full Parsing mode, the files are grabbed by starting at
the url specified and crawling through the site by finding
a link. This means you need to set two regular
expressions:
- The regular expression for the picture
- The regular expression that allows the parser to find
    the next link.
Note: if you run Full Parsing Mode for a specific comic,
and don't finish, it will pick up where it left off based
off the "next_url" file in that comic folder.


==Configuring==
Before you can run the cmcdwnlr, you should enter the main
script and set the variables.
In the "cmcdwnlr2.pl" file you'll find these variables to
set:
    $HOME: the location of the cmcdwnlr files
    $O_DIR: the place you want your comics stored
    $HEADER: if you're counting, how do you want your
        comics labeled? I went for Comic001.jpg etc. so I
        wrote "Comic"
    $CONF_FILE: the location of your comic configurations
    $BLANK_FILE: the location of your 'blank' image. In
        the case of a missing image on a page with
        counting. See 'skip_ahead'
There is also the "wget" command variable in the
"downloader.pl" file:
    $WGET_COMMAND: the command that runs wget. I added:
        --user-agent=Mozilla
        --tries=inf
        So that it appears as if wget is a browser, and it
        continues trying till the site is downloaded
If there are any better ideas, ideas that allow
flexibility and ease of use, I welcome them. Send me an
e-mail.


==Conf file==
The file is set up in the following format:
    COMICNAME:
        mode1=""
        mode2=""
The modes are predesignated, but the names are not. You can
chose any name for your comic. This name is the name of
the folder the comic will be saved in.
There are currently these Modes:
- url: the start url, or the "expression" for the
    images/pages
- pic: the regular expression for the image. When used the
    'url' will be assumed to be an "expression" for the
    page the image is located at.
- next: the regular expression for the next page. When
    used the 'url' will be assumed to be the start page.
    'pic' must also be assigned.
- get_text: if set to true (or almost anything else), then
    the title text (or mouse-over text) of the downloaded
    image, will also be gathered, and saved to
    $dir/$comic.title.$ext
    This option needs to have 'pic' set in order to
    function.
- double_urls: say a comic has 15 comics, and you visit
    the 16th. Sometimes comics give you a blank page (with
    no image to parse out) others give you the previous
    comic.
    In the latter case we don't want to download the comic
    again, so setting this option to true (or almost
    anything).
- tier: The comics are sorted by this. Tier 1 comics are
    downloaded first. then tier 2, etc.
- skip: When incrementing, occasionally comics are skipped.
    In the case of xkcd where the 404 did not have a comic,
    'skip' would look a designated number of pages, and see
    if there is a comic. If there is not, then it closes. If
    there is, it copies "$BLANK" as a placeholder. The
    placeholder is used so cmcdwnldr does not use bandwidth
    to try and download it again.
    When Parsing, sometimes a page is left blank for other
    reasons. If skip is labeled, then it will simply assume
    the parsing did not fail, and go to the next page.
Note: In both cases, a bad regular expression could trigger
skip. It's wise to make sure that you're regular expression
is lax enough, and sometimes even go to the website in the
browser to make sure nothing is missed.


=='url' expressions==
In the case where you are using the "counting" downloader,
the url will contain a number. In order to allow cmcdwnlr
to insert the number, use a {} to show location. The
contents of the brackets will change depending on the
"padding"
    1-9999  : {0} effectively turning off padding:
        ex:         http://comic-wo-padding.com/{0}.png
        will catch: http://comic-wo-padding.com/1.png
        and:        http://comic-wo-padding.com/99.png
        but not:    http;//comic-wo-padding.com/09.png
    001-999 : {3} pad the numbers to three:
        ex:         http://comic-w-padding.com/{3}.png
        will catch: http://comic-w-padding.com/001.png
        and:        http://comic-w-padding.com/999.png
        but not:    http://comic-w-padding.com/0001.png
        or:         http://comic-w-padding.com/1.png


=='pic'/'next' expressions==
It's a wise idea to look up regular expressions. Since
it's easy to mess up on the expression, testing is a good
idea. Try using 'regex_tester.pl' to test your see if
your expression will work.
The actual link, or picture, should be enclosed in the
first group of parens. Parenthesis can be used to enclose
other portions of text (and even nested), but the first
enclosed group of text will be assumed to be the
link/picture to act upon.


==Acting on URLS==
Since many sites embed relative links, cmcdwnlr will act
upon the parsed url/picture as if it is in the browser.
ie:
    if the path is of the form:
        /path/to/file
    then it will be counted as a domain link
    if the path is of the form:
        path/to/file
    then it will be counted as a relative link from the
    current page.
    if the path is of the form:
        http://comic.com/path/to/file
    then it will be counted as a new link entirely.
It should be noted, that even if a website says that the
file is a gif, cmcdwnlr will use imagemagick to determine
the file's actual file type.


==Start of Downloading==
Downloading stats differently depending on which mode:
-Counting Mode: In this case, the downloader looks for the
    first file in the folder, and pulls out the number,
    stripping any leading zeros. This number is used to
    continue the downloading. Then it checks each number
    to see if the file is downloaded already. If it is
    missing from the folder, it will download it.
-Parsing Mode: If the designated comic has already been
    run, it will have a "next_url" file saved. This file
    contains the url to continue from. From there it gets
    the page, checks the url, sees if the file is already
    in the folder, and if not, downloads it.


==Tricks of Downloading==
This is the place where I comment on some of the tricks
cmcdwnlr uses when downloading.
1) Wget allows for more flexibility with downloading:
    - infinite re-tries
    - telling the server it's a web browser
2) Sometimes websites embed a jpg file (for example) but
    call it a gif. This means when downloading, if the
    extension is saved as a gif file, programs won't be
    able to open it.
    Identify (part of the imagemagick package) allows
    identification of the image, so the correct extension
    will be applied at the end.


==End of Downloading==
Cases where downloading ends:
1) If the header of 'url' returns a 404, exit. In the case
    it does not, it's assumed that there's a picture
    inside, or it is the picture.
2) If after parsing with 'pic' or 'next' no path is found:
    exit.
3) If after parsing with 'next' the url parsed is the
    same: exit.
4) If double_urls is set, and the links for the picture on
    both page 35 and page 36 match, then exit before
    downloading 36.


==Extras==
In the folder is a Bash script called 'cberizer'. The
purpose of it is to create comic books of your downloaded
comics. It uses the zip format. It has has been not been
tested by anyone other then me. Use at your own risk.
That being said, the file should not (used loosely) delete
comics. It only moves them to a folder so that they can
later be restored.
You will need a comic book reader in order to open the
files. Of course, evince works for this.
There is also a 'regex_tester.pl' tool that can be used
to help find the right expression for downloading. Keep
in mind that it's useful to test more then one page before
you decide that the expression is good enough.

==Bug Reports==
Bug reports without the 'conf' file will be ignored.
Please include any and all cmcdwnlr output when the error
occurs.

```

---

