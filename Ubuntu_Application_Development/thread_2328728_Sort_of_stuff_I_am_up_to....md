---
title: "Sort of stuff I am up to..."
date: 2016-06-23
forum: Ubuntu Application Development
---

### Post by xen3 on 2016-06-23
Here is a screenshot of something I am working on this time:


[[IMG]http://www.xen.dds.nl/f/i/screenshots/downloader-tool-screenie_small.png[/IMG]]("http://www.xen.dds.nl/f/i/screenshots/downloader-tool-screenie.png")

(Click to enlarge).

It is a ridiculous thing meant to automate download processes for files you want to both have available as something you can regenerate (saving the URLs for files on your system) as well as the tool that does the regeneration; so if anything goes wrong, and you loose a lot of stuff, but you still have the config files and the tool, you can just run it and everything that you once obtained from the public Web, and that is still there, will be automatically recovered for you :p.

The program is just a Bash script with an automated job scheduler :p. It allows a maximum number of jobs that you can define, and has (or will have) support for extra operations such as file or directory extraction, and possibly even the running of scripts if possible. No matter how far fetched as this point. So supposing you want to take that 1.6GB source file, extract only a small part of it (like the Linux tree) and then recompress it using something else (or the same) -- you can do it. The purpose is having systems that are as much auto-configuration as possible, and having to do as little manual work as possible.

It is not exactly make-file material, not yet, but..... I hope to be able to define basic operations, mostly untarring stuff, repacking it or repackaging it elsewhere, perhaps even running predefined "make" or "configure" scripts. In this way you can have a script encoded as a config file, that will describe for you where to fetch the data, and what to do with it. It would have support for creating a temporary directory to work in, etc. Then you can have compilation of "hard to get" programs like that. It is not meant for personal configuration though; this is not meant for anything that could be sensitive. Really.

You could imagine downloading music with it, but this thing is meant for Linux archives mostly. So in the end it might have a GUI that would at least output the output of the script, and allow for better job control and monitoring (particularly status of background jobs).

Currently the thing just forks itself 4 times (I only have 4 jobs defined) but if you lower the number of allowed jobs, it will wait until a job slot is available before starting a new job :p. That is mostly meant to get more out of download multi-threading because downloads can block, and I don't want anything to block in this thing.

I guess the most "interesting" thing is how it obtains data:

```
curl_obtain_data() {
    curl -ILs -w "Final-Url: %{url_effective}\\nHttp-Code: %{http_code}\\n" "$1" | tr -d '\r' | tac | sed '3d' | sed '/^$/q' | sed '$d' | grep -E '^(Http-Code|Final-Url|Last-Modified|Content-Length):'
}
```

This script will just obtain the 4 url parameters that I want: Http-Code (only 200 is really useful, in the end), the Final-Url (many download sites will redirect you a number of times), the Content-Length (we could verify this against the download) and the Last-Modified date, (idem). Then I will use a currently rather simple thing to extract parameters out of it:

```
extract() {
    cat "$1" | { while read a b; do
        if [ "${a%:}" = "$2" ]; then res=$b; fi
    done; echo "$res"; }
}
```

This will either work on a file, or on stdin (specify "-" as the parameter). It will return the last parameter that matches.


The file has the following structure:
```

job-forked-routine() { }

{ parameter redirection to execute fork routine when called with certain parameter }

routines to the various job lists (bash arrays): a list for PID, a list for job number, a list for sequential ID, a list for the pointer in the status files, 
normally you would throw all of that in an object and use a list of those objects as that thing, but I have to create individual arrays out of everything.

The most congenious thing is that the array indexes themselves are in an array: they map array[$i] -> $i.
```

Bash allows you to iterate over existing elements easily, either across all elements, empty strings or not (for f in "${arr[@]}"; do), or by skipping those empty strings even though they are not unset; for, for bash, there is a difference between an "empty" element and an unset element.

When I iterate over the index array, I get the indexes to the elements of all others arrays. That means I obtain all my valid indexes, in that way. I could never "simultaneously" iterate over all (the way you could with objects) so instead I obtain all the indexes and use that to directly reference the elements of the other arrays.

Meanwhile I have some nifty sed work now and then, and some awk, but even though Bash is very slow, it is often faster to do something yourself, after all.

(Depends on how big the arrays are, Bash becomes really slow when arrays become bigger).

```
Functions to manipulate the job arrays
Function to output messages generated by the children
Function to generate progress updates (for downloads) mostly just generated from files on disk

And then of course the main loop.
```

Perhaps the main loop is the most interesting thing, but it is rather poor, I think. Still, it works. For now.

I redirect my background clients (my forks, children) to a file where their stdout gets put. Then, I just maintain a line pointer to distinguish which lines I have already read. Then I just open the file for reading, skip to the next line (with sed) and output everything that hasn't been processed yet. I prefix it or transform it using my own preferences (such as prefixing it with the child sequence number).

The clients also generate status messages that have the form of "KEY VALUE" so I know what state they are in :p. The system it has to run on doesn't have a "sleep" that can do more than (or smaller than) 1-second waits, but that means my clients get to have their say once every second.

Well, if no one finds this interesting anymore by now, that's fine by me, I don't find my writing interesting either ;-). Regards.

---

