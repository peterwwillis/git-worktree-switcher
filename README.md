# git-worktree-switcher (gw)

`gw` is a Bash wrapper around `git worktree` that uses `dialog` to provide
simple, TUI-driven workflows for switching between worktrees, adding new
worktrees, converting a repo into a worktree-friendly layout, and listing
worktrees. It is designed to be sourced into your shell so it can `cd` into
selected worktree directories.

## Features

- **Switch** between worktrees with a menu, including an indicator for the
  current branch and optional date sorting.
- **Add** a worktree, optionally creating a new branch.
- **Convert** a single-branch repo into a worktree-compatible directory layout.
- **List** existing worktrees in a dialog view.

## Requirements

- `git`
- `dialog`
- Bash (compatible with older Bash 3.x features)

## Installation

1. Copy `gw.sh` somewhere on your system.
2. Source it in your shell:

```bash
source /path/to/gw.sh
```

## Usage

Once sourced, use the `gw` command:

```bash
gw [COMMAND]
```

### Interactive mode

Run without arguments to open the TUI menu:

```bash
gw
```

### Commands

- `switch` (or `sw`) – Select and switch to a worktree directory.
- `add` (or `a`) – Add a new worktree, optionally creating a new branch.
- `convert` – Convert the current repo into a worktree-compatible layout.
- `remove` – Remove the currently checked-out worktree after switching to another.
- `list` – List current worktrees.

### Example workflow

1. Create a parent directory and clone the repo into a branch-named subdir:

```bash
mkdir foo
cd foo
git clone <repo-url> main
cd main
```

2. Source the script and run `gw`:

```bash
source /path/to/gw.sh
gw
```

3. Choose a command from the menu (switch, add, convert, remove, list).

## Configuration

- `GW_SORT_MODE`: Controls the order of the switch menu.
  - `default` (git's default order)
  - `date` (by last commit date, newest first)

Example:

```bash
export GW_SORT_MODE=date
```

## Notes

- `gw` must be sourced (not executed) so it can change your current directory.
- `convert` will move all files (including `.git`) into a branch-named
  subdirectory and leave a `.gwrc` marker in the parent directory.

## License

See [LICENSE](LICENSE).
