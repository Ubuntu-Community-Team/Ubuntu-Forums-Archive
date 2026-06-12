---
title: "recoll error on every image/jpeg file"
date: 2020-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by scott-mischko on 2020-04-26
I'm using Ubuntu 20.04 LTS.
Recoll is indexing my files. 
I see these all over the logs:
:2:internfile/mh_execm.cpp:89::MHExecMultiple: getline error
:2:internfile/mh_execm.cpp:89::MHExecMultiple: getline error
:2:internfile/internfile.cpp:797::FileInterner::internfile: next_document error [/mnt/SSD860EVO1/GoogleDrive/rpg/pulp/congress/Justice/2_7.jpg] image/jpeg 
:2:internfile/internfile.cpp:797::FileInterner::internfile: next_document error [/mnt/SSD860EVO1/GoogleDrive/rpg/pulp/congress/Justice/1_2.jpg] image/jpeg 
:2:internfile/mh_execm.cpp:89::MHExecMultiple: getline error
:2:internfile/internfile.cpp:797::FileInterner::internfile: next_document error [/mnt/SSD860EVO1/GoogleDrive/rpg/pulp/congress/Justice/3_10.jpg] image/jpeg 
:2:internfile/mh_execm.cpp:89::MHExecMultiple: getline error
:2:internfile/mh_execm.cpp:89::MHExecMultiple: getline error
:2:internfile/internfile.cpp:797::FileInterner::internfile: next_document error [/mnt/SSD860EVO1/GoogleDrive/rpg/pulp/congress/Justice/3_2.jpg] image/jpeg 
:2:internfile/internfile.cpp:797::FileInterner::internfile: next_document error [/mnt/SSD860EVO1/GoogleDrive/rpg/pulp/congress/Justice/1_7.jpg] image/jpeg 

Web search is not yielding answers.
Does someone here know what's going on with this or where I should look/ask?

Thanks!
Scott

---

### Post by TheFu on 2020-04-26
i would check that the helper tools recoll needs are installed.  There's a menu option that will show those tools as missing.

---

