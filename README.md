# Teknoseyir Clonner
 Clones Teknoseyir Posts to MongoDB
# Teknoseyir Clonner

This repository contains a Node.js script that clones Teknoseyir posts to MongoDB.

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/tuhalf/Teknoseyir-Clonner.git
    ```

2. Install the dependencies:

    ```bash
    npm install
    ```

## Usage

1. Set up your MongoDB connection by modifying the connection string in the `index.js` file.

2. Run the script:

    ```bash
    node index.js
    ```

### Continuing from a post

lastPostId is stored in the `lastPostId.txt` file. Script automatically reads the lastPostId from the file and continues from there. If you want to start from the beginning, set the lastPostId to 0.

If you want to continue from a specific post, set the lastPostId to the post id you want to continue from.

### Updating clonned posts

When a post is already clonned, it will update the post in the database. To make sure that you are storing the latest version of the post, you can run the script multiple times until the website is down.

## Database scheme

### Mongo Scheme
```json
{
    _id: {
        type: String,
        required: false
    },
    dateTime: {
        type: Date,
        required: false
    },
    author: {
        name: {
            type: String,
            required: false
        },
        username: {
            type: String,
            required: false
        },
        avatar: {
            type: String,
            required: false
        }
    },
    content: {
        type: String,
        required: false
    },
    tags: {
        type: [String],
        required: false
    },
    images: [
        {
            image: {
                type: String,
                required: false
            }
        }
    ],
    likes: {
        type: Number,
        required: false
    },
    shares: {
        type: Number,
        required: false
    },
    comments: [
        {
            _id: {
                type: String,
                required: false
            },
            dateTime: {
                type: Date,
                required: false
            },
            author: {
                name: {
                    type: String,
                    required: false
                },
                username: {
                    type: String,
                    required: false
                },
                avatar: {
                    type: String,
                    required: false
                }
            },
            content: {
                type: String,
                required: false
            },
            likes: {
                type: Number,
                required: false
            },
            images: [
                {
                    image: {
                        type: String,
                        required: false
                    }
                }
            ],
            replies: [
                {
                    _id: {
                        type: String,
                        required: false
                    },
                    dateTime: {
                        type: Date,
                        required: false
                    },
                    author: {
                        name: {
                            type: String,
                            required: false
                        },
                        username: {
                            type: String,
                            required: false
                        },
                        avatar: {
                            type: String,
                            required: false
                        }
                    },
                    content: {
                        type: String,
                        required: false
                    },
                    likes: {
                        type: Number,
                        required: false
                    },
                    images: [
                        {
                            image: {
                                type: String,
                                required: false
                            }
                        }
                    ],
                }
            ]
        }
    ]
}
```

### Example post
```json
{
  "_id": "1692187",
  "dateTime": {
    "$date": "2023-11-30T17:19:06.000Z"
  },
  "author": {
    "name": "Ronnie Kray",
    "username": "ronnie-kray",
    "avatar": "https://teknoseyir.com/wp-content/uploads/2023/11/171e68053c449b1.png"
  },
  "content": "#TSMetalcileri\n    \n    Ahanda benim tasarımım 😂\n      \n    Yapay zekaya hazırlattım ben valla 😀\n      \n    https://youtu.be/25Wgpi7JVaY?si=GWn1cfjzg5Oyvz-z",
  "tags": [
    "#TSMetalcileri",
    "Ahanda benim tasarımım 😂",
    "Yapay zekaya hazırlattım ben valla 😀",
    "https://youtu.be/25Wgpi7JVaY?si=GWn1cfjzg5Oyvz-z"
  ],
  "images": [
    {
      "image": "https://teknoseyir.com/wp-content/uploads/2023/11/69e9442d094f759.jpeg",
      "_id": {
        "$oid": "6568f3f9784034c7a3459a77"
      }
    }
  ],
  "likes": 721,
  "shares": 0,
  "comments": [
    {
      "_id": "6063242",
      "author": {
        "name": "ARMv7",
        "username": "armv7Ronnie Kray",
        "avatar": "https://teknoseyir.com/wp-content/uploads/2021/06/7fe4771c008a22e-250x250.jpg"
      },
      "content": "Ahanda benim tasarımım 😂\n      \n    Yapay zekaya hazırlattım ben valla 😀",
      "likes": 21,
      "images": [],
      "replies": []
    },
    {
      "_id": "6063243",
      "author": {
        "name": "Ronnie Kray",
        "username": "ronnie-kray",
        "avatar": "https://teknoseyir.com/wp-content/uploads/2023/11/171e68053c449b1.png"
      },
      "content": "Yapay zekaya hazırlattım ben valla 😀",
      "likes": 1,
      "images": [],
      "replies": []
    },
    {
      "_id": "6063251",
      "author": {
        "name": "Tunç Karesioğlu",
        "username": "tunc-karesi",
        "avatar": "https://secure.gravatar.com/avatar/235e81c3db67e2ef2a594bb0fa845d27?s=96&d=mm&r=g"
      },
      "content": "https://youtu.be/25Wgpi7JVaY?si=GWn1cfjzg5Oyvz-z",
      "likes": 0,
      "images": [],
      "replies": []
    }
  ],
  "__v": 0
}
```
