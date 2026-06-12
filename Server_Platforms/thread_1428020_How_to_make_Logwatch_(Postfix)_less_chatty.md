---
title: "How to make Logwatch (Postfix) less chatty"
date: 2010-03-12
forum: Server Platforms
---

### Post by nikolaidis on 2010-03-12
Hi all,

Does anyone know the trick to getting Logwatch to make its entries a
little less chatty and leave out the "Detailed" section of the Postfix
report? I can't seem to tone it down and the daily reports I get include
every recipient, host, etc., which is too much info to make a summary
report useful.

The first portion I get looks like this:

****** Summary *************************************************

       9   *Warning: Pre-queue content-filter connection overload
       2   SASL authentication failed
     432   Miscellaneous warnings

  46.833M  Bytes accepted                        49,107,749
  47.388M  Bytes delivered                       49,690,261
 ========   ================================================

    1451   Accepted                                  26.64%
    3995   Rejected                                  73.36%
 --------   ------------------------------------------------
    5446   Total                                    100.00%
 ========   ================================================

     624   Reject relay denied                       15.62%
     717   Reject unknown user                       17.95%
    2654   Reject RBL                                66.43%
 --------   ------------------------------------------------
    3995   Total Rejects                            100.00%
 ========   ================================================

    3800   Connections made
     687   Connections lost
    3799   Disconnections
    1440   Removed from queue
     880   Delivered
     820   Sent via SMTP
       5   Forwarded
      26   Deferred
     242   Deferrals
       4   Bounce (local)
     104   Bounce (remote)
       3   Expired and returned to sender
      63   DSNs undeliverable

      22   Timeout (inbound)
       2   Illegal address syntax in SMTP command
       6   Numeric hostname
       4   SMTP commands dialog error
     916   Hostname verification errors
       3   Hostname validation error
      21   Enabled PIX workaround
      70   SASL authenticated messages


This would be fine for a quick review that I do first thing. However,
the "Detailed" portion that follows is over 2,800 lines long!

Thanks,

Peter

---

### Post by Ilalmi on 2010-03-12
Hi,

is switching to postfix-logwatch ([http://www.mikecappella.com/logwatch/](http://www.mikecappella.com/logwatch/)) a possibility?

From the man page ([http://www.mikecappella.com/logwatch/postfix-logwatch.1.html):](http://www.mikecappella.com/logwatch/postfix-logwatch.1.html):)
> The postfix-logwatch utility produces a Summary section, a Detailed section, and additional report sections.  With level less than 5, postfix-logwatch will produce only the Summary section. At level 5 and above, the Detailed section, and any additional report  sections are candidates for output. Each incremental increase in level generates one  additional  hierarchical sub-level of output in the Detailed section of the report.

---

### Post by Mr. C. on 2010-04-24
FYI: postfix-logwatch and amavis-logwatch have moved to SourceForge:

[http://logreporters.sourceforge.net/](http://logreporters.sourceforge.net/)
[https://sourceforge.net/projects/logreporters/](https://sourceforge.net/projects/logreporters/)

---

