---
title: "[SOLVED] Minor Error in ThunderNewVersion Document???"
date: 2007-08-02
forum: Ubuntuzilla
---

### Post by 4WoofGrrrr on 2007-08-02
If this is not the correct place to discuss this document, please accept my apologies.

I recently installed thunderbird 2.0.0.6 using the document as a guide.  I didn't use the Ubuntuzilla script because I had already downloaded 2.0.06 when I learned of Ubuntuzilla, and every time I tried Ubuntuzilla it wanted to download again, even though I had copied the .tar.gz file to /tmp as suggested.

Anyway, to the problem....

After installing as per ThunderNewVersion, when I tried to launch thunderbird from the menus, or from QuickLauncher, nothing happens.  SO I tried to launch mozilla-thunderbird from the command line, and got this error message:

     run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin

To fix this, I ran the following commands:

    cd /opt/thunderbird
    sudo ln -s thunderbird-bin mozilla-thunderbird-bin


I didn't see a way to suggest a change to the ThunderNewVersion Document, so I thought I'd post this here.



Thanks.

---

### Post by nanotube on 2007-08-02
thanks for pointing that out. that symlink is required if you start as "mozilla-thunderbird", but if you start as just "thunderbird" everything works fine.
the ubuntuzilla script makes that symlink automatically, but the manual instructions were missing it... so i added it. :) 
i don't think this is really the "right" place to put notes about the wiki page, but it worked this time, so i guess it's all good. :)

also, about ubuntuzilla still insisting on downloading: how so? did you actually see it start the downloading, with the progress bar and everything?

---

