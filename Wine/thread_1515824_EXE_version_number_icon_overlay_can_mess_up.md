---
title: "EXE version number icon overlay can mess up"
date: 2010-06-22
forum: Wine
---

### Post by demonfoo on 2010-06-22
Hey all,

I've recently upgraded to the Wine 1.2rc4 packages on my lucid machines, and found the new "gnome-exe-thumbnailer" package pretty cool. That said, there is a potential issue with the version string that comes out of some EXE files.

I've found that, at least with some EXEs (particularly the EXE files for Telltale's game installers - yes, I love me some Sam & Max), the version string can end up being what I assume is some sort of templated string. For example, I looked in the gnome-exe-thumbnailer.sh script to figure out how it was extracting the version string from the EXE file, and discovered this:

```

$ wrestool --extract --raw --type=version ~/Downloads/SamMax303_PC_Setup.exe | tr '\0' '\t' | sed 's/\t\t/#/g' | tr -c -d '[:print:]' | sed -r 's/.*Version#*([^#]*).*/\1/; s/, /./g;' | xargs echo | sed -r 's/^([0-9]*\.[0-9]*\.[0-9]).*/\1/'
${PRODUCT_VERSION_DATE}

```

Yes, the string that comes out of that is, in fact, "${PRODUCT_VERSION_DATE}". I've attached an altered version of gnome-exe-thumbnailer.sh script that calls on 'grep' to check for a leading '$' in the output of the version string extraction pipeline, and doesn't try to composite in the version string if there is one. Don't know if this is a common thing, but I thought it was a worthwhile change to make.

Thanks, and keep up the good work.

---

