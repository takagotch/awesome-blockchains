### awesome-blockchains
---
https://github.com/openblockchains/awesome-blockchains

```
[#<Block:0xleed2a0
   @timestamp = ,
   @data = "",
   @previous_hash = "",
   @hash = "">,
 #<Block:0x1eec9a0
   @timestamp = ,
   @data = "",
   @previous_hash = "",
   @hash = "">,
 ]
```

```rb
// blockchai.rb
def calc_hash
  sha = Digest::SHA256.new
  sha.update( @timestamp.to_s + @previous_hash + @data )
  sha.hexdigest
end

//
class Block

  attr_reader :timestamp
  attr_reader :data
  attr_reader :hash
  
  def initialize(data, previous_hash)
    @timestamp = Time.now
    @data = data
    @previous_hash = prevous_hash
    @hash = calc_hash
  end
  
  def self.first( data="Genesis" )
    Block.new( data, "0000" )
  end
  
  def self.next( previous, data="Transaction Data..." )
    Block.new( data, previous.hash)
  end

private 

  def calc_hash
    sha = Digest::SHA256.new
    sha.update( @timestamp.to_s + @previous_hash + @data )
    sha.hexdigest
  end

end

b0 = Block.fist( "Genesis" )
b1 = Block.next( b0, "Transaction Data..." )
b2 = Block.next( b1, "Transaction Data..." )
b3 = Block.next( b2, "More Transaction Data...")

blockchain = [b0, b1, b2, b3]

pp blockchain

//
def compute_hash_with_of_work( difficulty="00" )
  nonce = 0
  loop do
    hash = calc_hash_with_nonce( nonce )
    if hash.start_with?( difficulty )
      return [nonce,hash]
    else
      nonce += 1
    end
  end
end

def calc_hash_with_nonce( nonce=0 )
  sha = Digest::SHA256.new
  sha.update( nonce.to_s + @timestamp.to_s + @previous_hash + @data )
  sha.hexdigest
end


```

```

```


