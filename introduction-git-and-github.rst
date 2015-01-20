:title: Introduction workshop Git & Github
:author: David Heijkamp
:keywords: git, github, version control, workshop
:css: css/presentation.css


----

Introduction workshop Git & Github
==================================

----

Introduction
============

Git: Distributed Version Control System
Github: Webservice met “centrale” repositories en aanverwante functionaliteit als issues, wiki en pull requests.
Praktisch:

Introductie / inleiding
Wat gaan we vandaag doen?

----

Agenda
======

* Introduction

  * Version control
  * Git specifics
  * Subversion vs. Git
  * Github
  * Git Flow

* Getting started

  * Installation
  * Configuration

* Basic operations

  * init
  * clone
  * ...

* Working with Git Flow

----

Version control
===============

Wat is version control?
“Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.”
Van Local naar Centralized naar Distributed
http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control 

----

Git
===

Maintains snapshots of a directory’s contents

----

Repository
==========

A repository is a collection of *commits*,

each of which is an archive of what the project's *working tree* looked like at a past date, whether on your machine or someone else's.

It also defines *HEAD* (see below), which identifies the branch or commit the current working tree stemmed from. 

Lastly, it contains a set of *branches* and *tags*, to identify certain commits by name.


----

The index
=========

Unlike other, similar tools you may have used, Git does not commit changes directly from the working tree into the repository.

Instead, changes are first registered in something called the index. Think of it as a way of “confirming” your changes, one by one, before doing a commit (which records all your approved changes at once).

Some find it helpful to call it instead as the “staging area”, instead of the index.

----

The index is an object store
============================

Objects are stored in ``.git/objects``

Check what files are in the git index:

.. code:: sh

    $ git ls-files --stage

Show a file based on the file's hash:

.. code:: sh

    $ git show 9c3f02f390174a28cbe9fc3d05285fe4a19b664e
    Copyright (C) 2015 Stichting Naturalis Biodiversity Center

You can usually abbreviat the hash to the first 6 or so characters:

.. code:: sh

    $ git show 9c3f02
    $ git show 9c3f

An older version of the same file can be shown as well:

.. code:: sh

    $ git show 07d596
    Copyright (C) 2013 Stichting Naturalis Biodiversity Center

----

Working tree
============

A working tree is any directory on your filesystem which has a repository associated with it (typically indicated by the presence of a sub-directory within it named ``.git``).

It includes all the files and sub-directories in that directory.

----

Commit
======

A commit is a snapshot of your working tree at some point in time.

The state of HEAD (see below) at the time your commit is made becomes that commit’s parent. This is what creates the notion of a “revision history”.

----

A commit and its tree
=====================

.. image:: img/commit-and-tree.png
    :height: 400px

----

Branch
======

A branch is just a *name for a commit*, also called a reference. It’s the parentage of a commit which defines its history, and thus the typical notion of a “branch of development”.

Branching means you diverge from the main line of development and continue to do work without messing with that main line.

----

Tag
===

A tag is also a name for a commit, similar to a branch, except that it always names the same commit, and can have its own description text.

----

Master
======

The mainline of development in most repositories is done on a branch called “master”. Although this is a typical default, it is in no way special.

----

HEAD
====

HEAD is used by your repository to define what is currently checked out:

* If you checkout a branch, HEAD symbolically refers to that branch, indicating that the branch name should be updated after the next commit operation.

* If you checkout a specific commit, HEAD refers to that commit only. This is referred to as a detached HEAD and occurs, for example, if you check out a tag name.

----

Subversion vs. Git
==================

Wat zijn de verschillen met Subversion?

----

Workflows
=========

Uitgangspunt:
Github Flow / Feature Branch Workflow
Gitflow
“Anything in the master branch is always deployable”
Shared repository model

Branching is a core concept in Git
Git really changed the way developers think of merging and branching.

----

Getting started
===============

----

Installing Git
==============

Instructions for Linux
----------------------

#. Open a terminal
#. Install git with the package manager of your distro:

   .. code:: sh

       $ apt-get install git
       $ yum install git
       $ pacman -S git

Instructions for Windows
------------------------

#. Download Github for Windows: https://windows.github.com
#. Click the downloaded file to start installation
#. Confirm installation
#. Fill in your credentials

Instructions for Mac
--------------------

#. Download Github for Mac: https://mac.github.com/
#. Click the downloaded file and confirm to open the downloaded file
#. Fill in your credentials
#. Click the option to install the Command Line tools

----

Git configuration
=================

Configuration of Git repo's and client is stored in several places:

* On Github (access etc.)
* In ``/etc/gitconfig``
* ``~/.gitconfig`` or ``~/.config/git/config``
* ``.git/config`` in each repository

Before getting started you need to configure some basics (you're covered when using Github for Mac / Windows):

.. code:: sh

    $ git config --global user.name "John Doe"
    $ git config --global user.email johndoe@example.com

Check for more info:
http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

----

Basic operations
================

Throughout the workshop we'll use:

* The command line interface (CLI) for Git
* The webinterface for Github
* The Github for Mac / Windows application
* ``github.com/workshop-naturalis`` as Github organization

In practice your IDE of choice will probably support Git integration as well.

----

Initializing a repo
===================

Creating or initializing a repo can be done in multiple ways:

* Locally with your Git client:

    .. code:: sh

        $ mkdir example-repo
        $ cd example-repo
        $ git init

* On Github:

    .. image:: img/newrepo.png

* With Github for Mac / Windows:

  * Create repo by clicking on +
  * Choose 'Publish' to make the repo available on GitHub

----

Cloning
=======

Cloning (checking out) an existing repo on GitHub can be done in two ways:

* First, copy the URL of the repo:

    .. image:: img/clone.png

Next thing is to clone the repo using the copied URL:

* Locally with your Git client:

    .. code:: sh

        $ git clone https://github.com/workshop-naturalis/<naam>.git

* With Github for Mac / Windows:

  * Create repo by clicking on +
  * Choose 'Publish' to make the repo available on GitHub

----

Staging files
=============

Files in a working tree are not automatically part of the index. Stage them first:

.. code:: sh

    $ git add LICENSE


----

Commiting
=========

After adding or changing a file or multiple files you can commit your changes:

* Using the command line:

    .. code:: sh

        $ git commit sample.py -m 'Added a test script'

* Using Github for Windows:

    .. image:: img/commitgithubforwindows.png

----

Pulling and pushing
===================

.. code:: sh

    git pull

----

Branching
=========

.. code:: sh

    git checkout -b

----

Stashing
========

----

Pull requests
=============

https://help.github.com/articles/using-pull-requests 
http://git-scm.com/docs/git-request-pull 

----

Merging
=======

Git
Resolving conflicts
https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/ 
Niet mogelijk in de webinterface
http://stackoverflow.com/questions/14503517/simulating-conflict-in-git 

----

Releases
========

https://help.github.com/articles/creating-releases/

Github biedt, op basis van Git tags, een high level manier om met releases te werken:
https://help.github.com/articles/about-releases/
https://help.github.com/articles/creating-releases/

Github raadt aan om semantic versioning te gebruiken: 

http://semver.org/

----

Documentation
=============

`Github Help`
`Pro Git <http://git-scm.com/book/>`_
`Git from the Bottom Up <http://ftp.newartisans.com/pub/git.from.bottom.up.pdf>`_
`Git cheat sheet <https://github.com/tiimgreen/github-cheat-sheet>`_

Smart commits
https://confluence.atlassian.com/display/Cloud/Processing+JIRA+issues+with+commit+messages 


Overig
Wanneer start je een branch?
Wanneer je een significante wijziging van je functionaliteit

Wat commit je in master?
Hoe zorg je dat mergen niet heel lastig wordt als je na een tijd een branch willen mergen met master?

Cursus
Wat is het verschil tussen Git en Subversion branches?
Merge practices in Git en Subversion?

Voor welke wijzigingen gebruik je een commit? Sla je elke wijziging op in een commit of verzamel je een aantal wijzigingen die je vervolgens commit?
Zie voor een aardige benadering:
http://sethrobertson.github.io/GitBestPractices/#sausage
http://sethrobertson.github.io/GitBestPractices/#commit
