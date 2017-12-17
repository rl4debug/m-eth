# m-eth

## RLP format

Errs
```
ErrValueTooLarge : content size larger available buffer len
ErrUnexpectedEOF: do you want buffer avaialble? but buffer is zero bytes
ErrCanonSize: Reject strings that should've been single bytes.
Ex:
if contentsize == 1 && len(buf) > 1 && buf[1] < 128 {
			return 0, 0, 0, ErrCanonSize
		}
		
```

```go
type Kind int

const (
	Byte Kind = iota
	String
	List
)

func (k Kind) String() string {
	switch k {
	case Byte:
		return "Byte"
	case String:
		return "String"
	case List:
		return "List"
	default:
		return fmt.Sprintf("Unknown(%d)", k)
	}
}
```

Refer to `https://github.com/ethereum/go-ethereum/blob/c6069a627c42c21fc02d0770d39db9a9be45b180/rlp/raw.go#L86`

| Kind | TagSize | Content Size |
|------|---------|--------------|
| A | B | C |
