### Undoing Things ⚒
#### Using git amend, git reset and git restore
####  git amend
```console
$ git commit --amend
```
If you commit without adding all files, or you want to edit the commit message, use the git amend to redo the commit.
```shell
$ git commit -m 'Initial commit'
$ git add forgotten_file
$ git commit --amend
```
You end up with a single commit — the second commit replaces the results of the first.

✏️ Git amend pushes the old commit aside and places the new commit in its place.

Git amend is useful to do minor changes to your last commit and saves us from cluttering commit history and messages. 

✋⛔️ Amending previously pushed commits and force pushing the branch will cause problems for your collaborators. Only amend local commits that are not pushed anywhere.

###### How to undo staged file?
#### git reset
```
git reset HEAD <file>…​
```
If you need to remove a file from staging area, use `git reset`.

For example, let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type `git add *` and stage them both.

⚠️☝ In this example file in the working directory is not touched. However, git reset command can be dangerous, especially when used with the `--hard` flag.

###### How to undo all the changes to a file, reverting it back to the last commit?
#### git checkout

```console
git checkout -- <file>...
```

To discard the changes you’ve made and revert it back to what it looked like when you last committed, use `git checkout`.
```shell
git checkout -- file_to_revert
```

☝️⛔️ Be careful with `git checkout`, any local changes you made to that file are gone — Git just replaced that file with the last staged or committed version.

💡 If you want to keep the changes to the file but still need to get it out of the way for now, use git stashing and branching instead.

##### How to undo things with git restore?
#### git restore

Git introduced restore command from version 2.23.0. Basically an alternative to `git reset`,  Git uses it for many undo operations now, replacing the `git reset`.

##### Undo staging
```console
git restore --staged <file>...
```

If you have staged two files but now want to commit them separately, use `git restore` to un-stage one of the file.
```shell
git restore --staged file_to_unstage
```

##### Discard file changes

```console
git restore <file>...
```

If you want discard changes to a file — revert it back to what it looked like when you last committed.

```shell
git restore file_to_revert
```

⚠️☝️ `git restore` replaces the file with the last staged or committed version. Any local changes you made to that file are gone.