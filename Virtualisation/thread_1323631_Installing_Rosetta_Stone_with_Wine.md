---
title: "Installing Rosetta Stone with Wine"
date: 2009-11-11
forum: Virtualisation
---

### Post by anarcholis on 2009-11-11
I am trying to install Rosetta Stone 3.2.11 from CD on Ubuntu 9.10 using Wine 1.0.1 (the basic version installed by synaptic package manager) set for Windows XP.

I would like to use Wine to install Rosetta Stone, so I'm focused on finding a solution using that, for now.

I run 'wine setup.exe' in the command line.First it prompts me for what language I want to run it in. After selecting english, I get:

```

fixme:advapi:LookupAccountNameW (null) L"hartigd" (nil) 0x33f864 (nil) 0x33f868 0x33f85c - stub
fixme:advapi:LookupAccountNameW (null) L"hartigd" 0x1316b0 0x33f864 0x1318b8 0x33f868 0x33f85c - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values

```

The install shield still runs. I select the directory to install to, then I get:

```

fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 10 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

The error window tells me that InstallShield was interrupted before installation could complete and that my system has not been altered.

I am not very familiar with Linux or Wine, but I would guess that the 'class not registered' errors are what is significant. This implies to me that I am missing some package or addon, or maybe it just means this version of Rosetta Stone is not supported. 

Can anybody help point me in the right direction as to a. what those error codes mean and b. what might be missing?

-Dan

---

