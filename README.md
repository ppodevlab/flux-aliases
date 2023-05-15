# flux-aliases

This repository contains [a script](generate_aliases.py) to generate hundreds of
convenient shell aliases for kubectl, so you no longer need to spell out every single
command and --flag over and over again.

An example shell alias created from command/flags permutation looks like:

    alias ksysgdepwslowidel='kubectl --namespace=kube-system get deployment --watch --show-labels -o=wide -l'

Confused? Read on.

### Examples

Some of the 500 generated aliases are:

```sh
alias f='flux'
alias fsys='flux --namespace=flux-system'
alias fm='flux --namespace=management'
alias fg='flux get'
alias fsysg='flux --namespace=flux-system get'
alias fmg='flux --namespace=management get'
alias frm='flux delete'
alias fsysrm='flux --namespace=flux-system delete'
alias fmrm='flux --namespace=management delete'
alias fr='flux reconcile'
alias fsysr='flux --namespace=flux-system reconcile'
alias fmr='flux --namespace=management reconcile'
alias fe='flux resume'
alias fsyse='flux --namespace=flux-system resume'
alias fme='flux --namespace=management resume'
alias fs='flux suspend'
alias fsyss='flux --namespace=flux-system suspend'
alias fms='flux --namespace=management suspend'
alias fhr='flux helmrelease'
alias fsyshr='flux --namespace=flux-system helmrelease'
alias fmhr='flux --namespace=management helmrelease'
alias fghr='flux get helmrelease'
...
```

See [the full list](.kubectl_aliases).

### Installation

You can directly download the [`.flux_aliases` file](https://rawgit.com/ahmetb/kubectl-alias/master/.kubectl_aliases)
and save it in your $HOME directory, then edit your .bashrc/.zshrc file with:

```sh
[ -f ~/.flux_aliases ] && source ~/.flux_aliases
```

**Print the full command before running it:** Add this to your `.bashrc` or
`.zshrc` file:

```sh
function flux() { echo "+ flux $@">&2; command flux $@; }
```

### Syntax explanation

* **`f`**=`flux`
  * **`sys`**=`--namespace kube-system`
* commands:
  * **`g`**=`get`
  * **`rm`**=`delete`
  * **`s`**:`suspend`
  * **`e`**:`resume`
  * **`r`**:`rconcile`
* resources:
  * **`sh`**=`helmrepository`, **`hr`**=`helmrelease`, **`k`**=`kustomization`, etc 
* flags:
  * output format: **`oyaml`**, **`ojson`**, **`owide`**
  * **`an`**: `--all-namespaces`
  * **`all`**: `--all`
* value flags (should be at the end):
  * **`n`**=`-n/--namespace`
  
### FAQ

- **Doesn't this slow down my shell start up?** Sourcing the file that contains
~500 aliases takes about 30-45 milliseconds in my shell (zsh). I don't think
it's a big deal for me. Measure it with `echo $(($(date +%s%N)/1000000))`
command yourself in your .bashrc/.zshrc.

-----

This is not an official Google project.
