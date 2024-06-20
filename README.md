# git-lfs
demo-of-git-lfs

https://git-lfs.com/


## Getting Started

1. Download and install the Git command line extension. Once downloaded and installed, set up Git LFS for your user account by running:

git lfs install

You only need to run this once per user account.

1. In each Git repository where you want to use Git LFS, select the file types you'd like Git LFS to manage (or directly edit your .gitattributes). You can configure additional file extensions at anytime.

git lfs track "*.psd"

Now make sure .gitattributes is tracked:

git add .gitattributes

Note that defining the file types Git LFS should track will not, by itself, convert any pre-existing files to Git LFS, such as files on other branches or in your prior commit history. To do that, use the git lfs migrate(1) command, which has a range of options designed to suit various potential use cases.

1. There is no step three. Just commit and push to GitHub as you normally would; for instance, if your current branch is named main:

git add file.psd
git commit -m "Add design file"
git push origin main

Check out our wiki, discussion forum, and documentation for help with any questions you might have!

## To create dummy file with specific size on Mac 

mkfile -n 100m 100mb.file


## Normal workflow with large file

### one time per file type
git lfs track "*.file"

### add the modified file to the staging area
git add 100mb.file
git add .gitattributes

### commit the file 
git commit -m 'initial commit with large file'

### push the file to github.com
git push origin main

```
❯ git push origin main
Uploading LFS objects: 100% (1/1), 105 MB | 1.4 MB/s, done.
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 12 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (8/8), 1.97 KiB | 1011.00 KiB/s, done.
Total 8 (delta 0), reused 3 (delta 0), pack-reused 0 (from 0)
To github.com:tchia04/git-lfs.git
 * [new branch]      main -> main


```


## git-lfs --help
```
❯ git-lfs --help
git lfs <command> [<args>]

Git LFS is a system for managing and versioning large files in
association with a Git repository.  Instead of storing the large files
within the Git repository as blobs, Git LFS stores special "pointer
files" in the repository, while storing the actual file contents on a
Git LFS server.  The contents of the large file are downloaded
automatically when needed, for example when a Git branch containing
the large file is checked out.

Git LFS works by using a "smudge" filter to look up the large file
contents based on the pointer file, and a "clean" filter to create a
new version of the pointer file when the large file's contents change.
It also uses a pre-push hook to upload the large file contents to
the Git LFS server whenever a commit containing a new large file
version is about to be pushed to the corresponding Git server.

Commands
--------

Like Git, Git LFS commands are separated into high level ("porcelain")
commands and low level ("plumbing") commands.

High level porcelain commands
-----------------------------

* git lfs checkout:
    Populate working copy with real content from Git LFS files.
* git lfs dedup:
    De-duplicate Git LFS files.
* git lfs env:
    Display the Git LFS environment.
* git lfs ext:
    Display Git LFS extension details.
* git lfs fetch:
    Download Git LFS files from a remote.
* git lfs fsck:
    Check Git LFS files for consistency.
* git lfs install:
    Install Git LFS configuration.
* git lfs lock:
    Set a file as "locked" on the Git LFS server.
* git lfs locks:
    List currently "locked" files from the Git LFS server.
* git lfs logs:
    Show errors from the Git LFS command.
* git lfs ls-files:
    Show information about Git LFS files in the index and working tree.
* git lfs migrate:
    Migrate history to or from Git LFS
* git lfs prune:
    Delete old Git LFS files from local storage
* git lfs pull:
    Fetch Git LFS changes from the remote & checkout any required working tree
    files.
* git lfs push:
    Push queued large files to the Git LFS endpoint.
* git lfs status:
    Show the status of Git LFS files in the working tree.
* git lfs track:
    View or add Git LFS paths to Git attributes.
* git lfs uninstall:
    Uninstall Git LFS by removing hooks and smudge/clean filter configuration.
* git lfs unlock:
    Remove "locked" setting for a file on the Git LFS server.
* git lfs untrack:
    Remove Git LFS paths from Git Attributes.
* git lfs update:
    Update Git hooks for the current Git repository.
* git lfs version:
    Report the version number.

Low level plumbing commands
---------------------------

* git lfs clean:
    Git clean filter that converts large files to pointers.
* git lfs filter-process:
    Git process filter that converts between large files and pointers.
* git lfs merge-driver:
    Merge text-based LFS files
* git lfs pointer:
    Build and compare pointers.
* git lfs post-checkout:
    Git post-checkout hook implementation.
* git lfs post-commit:
    Git post-commit hook implementation.
* git lfs post-merge:
    Git post-merge hook implementation.
* git lfs pre-push:
    Git pre-push hook implementation.
* git lfs smudge:
    Git smudge filter that converts pointer in blobs to the actual content.
* git lfs standalone-file:
    Git LFS standalone transfer adapter for file URLs (local paths).

Examples
--------

To get started with Git LFS, the following commands can be used.

 1. Setup Git LFS on your system. You only have to do this once per
    repository per machine:

        git lfs install

 2. Choose the type of files you want to track, for examples all ISO
    images, with git lfs track:

        git lfs track "*.iso"

 3. The above stores this information in gitattributes(5) files, so
    that file needs to be added to the repository:

        git add .gitattributes

 4. Commit, push and work with the files normally:

        git add file.iso
        git commit -m "Add disk image"
        git push


```
