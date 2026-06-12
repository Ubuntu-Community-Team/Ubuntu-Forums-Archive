---
title: "Python Google cloudprint error on thin client setup as print server"
date: 2014-06-24
forum: Server Platforms
---

### Post by treehuggerguy on 2014-06-24
I'm trying to create a print server for an MFC-7860DW. 

I've configured print drivers and CUPS, and printing works properly. After installing "cloudprint" using PIP, I get an error message.

Initially I had tried to use a Raspberry Pi, but the print drivers created by Brother didn't work on ARM and the drivers I found only sort of half worked. I did configure cloud print using python and it appeared to work properly. I've used the same instructions here, so I'm not sure why it's working differently.  Here's the error message:

> Traceback (most recent call last):
  File "/usr/local/bin/cloudprint", line 9, in <module>
    load_entry_point('cloudprint==0.11', 'console_scripts', 'cloudprint')()
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py", line 468, in main
    sync_printers(cups_connection, cpp)
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py", line 307, in sync_printers
    cpp.add_printer(printer_name, description, ppd)
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py", line 192, in add_printer
    { 'X-CloudPrint-Proxy' : 'ArmoooIsAnOEM'},
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py", line 141, in f
    r = attr(*arg, **karg)
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/rest.py", line 105, in post
    return self.rest_call('POST', path, data, content_type, headers, response_type)
  File "/usr/local/lib/python2.7/dist-packages/cloudprint/rest.py", line 58, in rest_call
    data = self.CONTENT_ENCODE[content_type](data)
  File "/usr/lib/python2.7/urllib.py", line 1332, in urlencode
    v = quote_plus(str(v))
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2019' in position 32: ordinal not in range(128)

Not having any experience with Python, I'm not sure what I'm looking at here. Anyone have a suggestion for how to fix this?

---

