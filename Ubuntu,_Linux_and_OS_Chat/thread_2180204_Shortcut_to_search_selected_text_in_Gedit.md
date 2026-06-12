---
title: "Shortcut to search selected text in Gedit"
date: 2013-10-12
forum: Ubuntu, Linux and OS Chat
---

### Post by kevinlyfellow on 2013-10-12
A friend was looking for a text editor that would provide a shortcut to searching the internet within the editor.  I managed to find a really cool plugin for Gedit: "External Tools".  This provides a bash scripting language for use with Gedit.

I had to learn a few things along the way, but I ended up with this script.

After enabling the plugin go to "Tools" -> "Manage External Tools" and make a new script.  Use the following:
```
#!/bin/sh

# Choose your browser
BROWSER="firefox" 
#BROWSER="iceweasel"
#BROWSER="epiphany-browser"
#BROWSER="x-www-browser"

# Choose your search engine
SEARCH_URL="https://duckduckgo.com/?q="
#SEARCH_URL="https://www.google.com/#q="
#SEARCH_URL="http://www.bing.com/search?q="

# The search engines all seem to use +
# to space the search terms
SEARCH_DELIMITER="+"

# Create the search string.  To work with
# multiple search terms, sed is used to
# replace the spaces with the delimiter
arguments="`xargs`"
search_var=`echo $arguments | sed 's/ /'$SEARCH_DELIMITER'/g'`

# Issue the command
$BROWSER $SEARCH_URL$search_var

```

The input needs to be set to "Current Selection" and choose your shortcut.

This also works in Pluma for you Mate users out there.
Enjoy.

---

