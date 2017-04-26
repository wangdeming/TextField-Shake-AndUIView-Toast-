# TextField-UIView-Toast
UITextField+Shake.h
#import <UIKit/UIKit.h>

@interface UITextField (Shake)

- (void)shake;

@end

UITextField+Shake.m

#import "UITextField+Shake.h"

/**
 * 为textField扩展一个左右晃动的动画
 */

@implementation UITextField (Shake)

- (void)shake {
    CAKeyframeAnimation *keyFrame = [CAKeyframeAnimation animationWithKeyPath:@"position.x"];
    keyFrame.duration = 0.3;
    CGFloat x = self.layer.position.x;
    keyFrame.values = @[@(x + 30), @(x - 30), @(x + 20), @(x - 20), @(x + 10), @(x - 10), @(x + 5), @(x - 5)];
    [self.layer addAnimation:keyFrame forKey:@"shake"];

}

@end

使用的话就直接[self.textField shake]就能实现UITextField晃动的效果。在账号和密码输入的时候可以进行使用。

UIView(Toast)的使用方法就是在当前view上使用如下方法：
- (void)makeToast:(NSString *)message;
- (void)makeToast:(NSString *)message duration:(NSTimeInterval)interval position:(id)position;
- (void)makeToast:(NSString *)message duration:(NSTimeInterval)interval position:(id)position image:(UIImage *)image;
- (void)makeToast:(NSString *)message duration:(NSTimeInterval)interval position:(id)position title:(NSString *)title;
- (void)makeToast:(NSString *)message duration:(NSTimeInterval)interval position:(id)position title:(NSString *)title image:(UIImage *)image;

如简单的[self.view makeToast:@"请输入账号或密码"];
