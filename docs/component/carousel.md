#### 基础用法

```javascript
<Carousel>
    <li className="item"><img className="img" src="//img1.qunarzz.com/qs/1610/a6/01d1ad00e4b9e102.jpg" /></li>  
    <li className="item"><img className="img" src="//img1.qunarzz.com/qs/1610/a6/01d1ad00e4b9e102.jpg" /></li>  
    <li className="item"><img className="img" src="//img1.qunarzz.com/qs/1610/a6/01d1ad00e4b9e102.jpg" /></li>  
</Carousel>
```

#### 使用内置组件CarouselItem

+ 提供图片懒加载功能
+ 配合css实现当前页切换的动画效果

```javascript
const testData = [
    {
        img: '//img.alicdn.com/tps/TB13Ha_NXXXXXbCXVXXXXXXXXXX-1125-352.jpg_q50.jpg'
    },{
        img: '//aecpm.alicdn.com/simba/img/TB1CWf9KpXXXXbuXpXXSutbFXXX.jpg_q50.jpg'
    },{
        img: '//aecpm.alicdn.com/simba/img/TB10CLcNXXXXXXVXXXXSutbFXXX.jpg_q50.jpg'
    },{
        img: '//gw.alicdn.com/imgextra/i2/5/TB2xuHoaX55V1Bjy0FnXXc5XFXa_!!5-0-yamato.jpg_q50.jpg'
    },{
        img: '//img.alicdn.com/tps/TB1XXrzNXXXXXaXXXXXXXXXXXXX-1125-352.jpg_q50.jpg'
    }
];
class Demo extends Component {
    constructor() {
        super();
        this.state = {
            currentPage: 1,
        };
    }

    render() {
        return (            
            <Carousel
                afterChange={(page) => {
                    this.setState({
                        currentPage: page
                    })
                }}
            >
            {
                testData.map((item, index) => (
                    <CarouselItem
                        index={index + 1}
                        key={index + 1}
                        currentPage={this.state.currentPage}
                        {...item}
                        pagesNum={testData.length}
                        lazyload
                    />
                ))
            }
            </Carousel>
        )
    }
}

```

#### 自定义动画
传入JS动画对象，使用自定义动画

```javascript
import aniCss from '~yo/component/carousel/src/aniCss.js';
class Demo extends Component {    
    constructor() {
        super();
        this.state = {
            currentPage: 1,
        };
    }

    render(){
        return (        
            <Carousel
                aniObj={aniCss}
                extraClass={'yo-carousel-fade'}
                afterChange={(currentPage) => {
                    this.setState({
                        currentPage
                    })
                }}
            >
            {
                testData.map((item, index) => (
                    <CarouselItem
                        index={index + 1}
                        key={index + 1}
                        currentPage={this.state.currentPage}
                        {...item}
                        lazyload
                        activeClass={'top'}
                        pagesNum={testData.length}
                    />
                ))
            }
            </Carousel>
        )
    }
}
```
