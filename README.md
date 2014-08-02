commentfilter
==========
Go package to provide a io.Reader that filters out comments.

Example
-------
```Go
package main

import (
	"bytes"
	"github.com/timob/commentfilter"
	"io"
	"os"
)

func main() {
	source := bytes.NewBufferString(
		`" /* here is a string literal */ \" " /* Here is a "comment" */ `,
	)
	filtered := commentfilter.NewCommentFilter("/*", "*/", `"`, `\`, source) 
	io.Copy(os.Stdout, filtered)
}
```

