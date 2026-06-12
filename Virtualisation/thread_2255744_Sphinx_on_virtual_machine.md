---
title: "Sphinx on virtual machine"
date: 2014-12-07
forum: Virtualisation
---

### Post by slo2 on 2014-12-07
I have virtual machine with ubuntu 14 installed on it. I am trying to build sphinx3 but at the point where i type 
$SPHINXBASE/bin/sphinx_fe -c raw_files -di wav/ -do feats/ -ei raw -raw yes -eo mfc

it gives me following error msg
SYSTEM_ERROR: "sphinx_fe.c", line 792: Failed to open control file raw_files; No such file or directory

I know there is some package missing but I cannot figure which one.... can you please help me out???

Thank you

---

### Post by ubfan1 on 2014-12-07
The error says you are missing the file raw_files (or maybe wav/raw_files, not sure how sphinx works with the -di).  With the ls command, do you see it? Try ls wav/* next and see it it's there.

---

### Post by bapoumba on 2014-12-07
*Thread moved to **Virtualisation*** and thread title edited.

---

### Post by raksa2 on 2014-12-08
just create new file name "raw_files" by [B]touch raw_files

[/B]don't forget to edit it by **vim raw_files **or **gedit raw_files**
> copy all names of wav files (without extension) in **./wav**
> Ex: wav/file1.wav wav/file2.wav >> file1 file2> put them to your [B]raw_file
[/B]> save and quit
then try it again

Good Luck

---

