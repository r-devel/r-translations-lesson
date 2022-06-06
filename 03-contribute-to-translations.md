---
title: "Contributing to Translations"
teaching: 45
exercises: 6
---

:::::::::::::::::::::::::::::::::::::: questions 

- How to translate messages, errors, warnings in R to another language?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explore the translations process in R
- Explore the translation tools available

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::: challenge

## Challenge 1: Check the progress of translations for a given language

The [check_progress.R](https://github.com/r-devel/translations-campfire/blob/main/check_progress.R) script provides a code to check progress for a given language, producing a table as follows.


```r
lang <- "de"  ## ISO code for the language of interest
library(devtools)
```

```{.output}
Loading required package: usethis
```

```r
po_status <- source_url("https://raw.githubusercontent.com/r-devel/translations-campfire/main/check_progress.R")
```

```{.output}
ℹ SHA-1 hash of file is ce6513224e87563d09fb3da80183b3484939636d
```

```r
knitr::kable(po_status$value)
```



||
||
||
||

:::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::: challenge

## Challenge 2: Exploring the translations tools

The following tools help during the translations process:

- Download the [Poedit tool](https://poedit.net/download) for translations.
- Keep an [online keyboard](https://www.lexilogos.com/keyboard/index.htm) handy.
- Explore a [mirror of the R source code](https://github.com/r-devel/r-svn), especially the `.po` and the `.pot` (template file) files in it.


:::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::: challenge

## Challenge 3: Standard English to British English

Demonstration of the conversion of `.pot` file available in Standard English to a `.po` file in British English. Follow the steps below to perform this conversion.

- Check the [TODO list for British English (en_GB)](https://github.com/r-devel/translations-campfire/issues/6), to know which files need work on the British English translations.
- Switch to the [en_GB branch](https://github.com/r-devel/translations-campfire/tree/en_GB).
- Look at example `.pot` and existing `.po` files.
- Open a `.pot` file of interest in RStudio.
- Explore the metadata in this `.pot` file and update it wherever required.
- When the .pot file is updated, one of the following happens:
  - A message is added: This would need translation.
  - A message is removed: This would be deprecated.
  - A message is changed: If this is a big change, then it is treated as new message added and old message deleted. Otherwise it is marked as “fuzzy”, which means that the translation needs updating.
- If a `.po` file does not exist corresponding to a `.pot` file, then a new one can be created using the following command (The command demonstrates creating a `.po` file for `French` (`fr`) language). 
```
msginit -i R-base.pot -o R-fr.po -l fr
```

- Some messages have [plural forms](https://developer.r-project.org/Translations30.html).

```
  msgid        "Warning message:\n"
  msgid_plural "Warning messages:\n"
  msgstr[0]    ""
  msgstr[1]    ""
```

In the message above, there are two `msgid` messages. For languages with a singular and only one plural, the first is for the singular form and the second is for the plural form. For languages which do not have plurals, give only one line starting with `msgstr[0]`. (The Slovenian language would need four lines.).

:::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::: challenge

## Challenge 4: Standard English to Hindi

Demonstration of the conversion of `.pot` file available in Standard English to a `.po` file in Hindi. Follow the steps below to perform this conversion.

- Check the [TODO list for Hindi (hi)](https://github.com/r-devel/translations-campfire/issues/7), to know which files need work on the Hindi translations.
- Switch to the [hi branch](https://github.com/r-devel/translations-campfire/tree/hi).
- Look at example `.pot` and existing `.po` files.
- Open a `.pot` file of interest in the [Poedit tool](https://poedit.net/download) for translations.
- Translate the messages from Standard English to Hindi one by one. Use an [online keyboard](https://www.lexilogos.com/keyboard/index.htm) to assist in the process of translations.
- If any translations needs further work then click on the `needs work` button on the Poedit tool. It will turn the message into orange coloured font on Poedit and it will be marked as `fuzzy` in the corresponding `.po` file.
- Download the corresponding `.po` and view it on RStudio to see the changes.
- Make sure, not to translate, variable names, function names, commands, package names, formats like %d, %s, %H, etc..
- If translation (in any of the `msgstr` of the `.po` file) is left as `""`, then the untranslated message (`msgid`) will be used.

:::::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::: challenge

## Challenge 5: Try your own translations!

Want to try translating to a language of your interest? Check the [open issues](https://github.com/r-devel/translations-campfire/issues) for a specific language on GitHub. Switch to the [corresponding language branch](https://github.com/r-devel/translations-campfire) on GitHub (named according to the ISO code). Open the files that need work and try your own translations.

:::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::: challenge

## Challenge 6: Bonus!

Some bonus tasks to work on!

1. Complete translations of the `.po` file(s) you started working on during this lesson. 
2. Check out any other package files that need a translation.
3. Translate in any other language of interest.
4. Check existing `.po` files that might need an update in the translations. 

::::::::::::::::::::::::::::::::::::::::::
